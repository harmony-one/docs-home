# Post-Mortem: OSTN Rolling Upgrade failure Mar 21, 2020

### Summary <a id="summary"></a>

‌On March 21, 2020 a Open Staking Testnet \(OSTN\) rolling upgrade commenced around 11:40 a.m. During the upgrade consensus was lost on Shard 0 due to a pre-existing nil pointer issue which was triggered by a view change. 

This caused \(or was compounded by\) an inability of nodes to synch to the highest block \(17080\) due to the fact that 4 out of the 5 nodes which for DNS entry api.s0.os.hmny.io were at a lower height \(17061\).

An attempt was made to bring all the DNS nodes to the same height, however the lower \(17061\) block height was chosen rather than the highest height 17080. This left shard 0 unable to recover and a hard refresh was required.

RJ, quickly investigated and resolved the cause of the underlying view chain. Leo then applied this change as well as all other changes in master to the t3 branch and a rolling upgrade began at around 15:00 which completed at approximately 16:00 p.m.  


### Customer Impact <a id="customer-impact"></a>

‌All OSTN validators \(primarily the p-ops team and harmony\) were unable to use OSTN for approximately 3 hours. Also a rolling upgrade became a hard refresh which requires all validators to reset their nodes. At this point in the OSTN lifecycle hard refreshes are a common occurrence and so the validators are prepared for this.

### People Involved <a id="people-involved"></a>

* John \(john@harmony.one\)
* Daniel \(daniel@harmony.one\)
* Leo \(leo@harmony.one\)
* RJ \(rongjian@harmony.one\)

### Timeline <a id="timeline"></a>

‌

**This outage happened on 2020-03-22 times are in PDT.**

* **11:09 - John confirmed build on team-devops and created pull request** [**2575**](https://github.com/harmony-one/harmony/pull/2575)\*\*\*\*
* 11:40 - John merged commit, informed p-ops and staking and began rolling upgrade
* 12:31 - Daniel identified issues with Shard 0 seen on watchdog
* 12:31 - 14:20 Following remediation steps took place
  * Daniel rolled back to last commit i.e. yesterday's version
  * Daniel restarted all shards 1,2 and 3 synched - shard 0 did not
  * Daniel noticed the leader and five others were on block 17080 everyone else on 17061, also one of the Nodes that supported api.os.hmny.io was at 17080 
  * Daniel changed the IPS for the DNS entry removing the node with 17080 and replacing it with another 17061 node
  * Daniel deleted 5 nodes dbs which were at 17080 allowing all to synch to 17061 ~ 1:00 pm \(take 80 mins to synch\)
  * Leo cloned the db to the nodes \(to speed up synching\)
  * RJ investigated the nil pointer issue and proposed [Merge Signing Fixes to T3](https://github.com/harmony-one/harmony/commit/6ff740ed647d81e9a8e677a26ffad0cfa7873b76) 
  * Leo, Daniel - After Cloning the DB’s consensus still could not be gained and blocks could not be produced on Shard 0
* 14:23 - Leo, RJ, Daniel, John made decision to do a hard refresh 
* **14:23  - John notified p-ops that a hard refresh was needed**
* 14:25 - Leo merged the latest code from Master into t3 see below
* 14:58 - John began deploying the hard refresh
* 15:08 - Protocol Upgrade Complete, Consensus Reached and Watchdog Updated
* 15:08 - 15:46 John, Daniel, Cem - Block Explorer Built, Faucet and Funding Launched, Validator build complete, Sentries Launched and Earning
* **15:46 - John - Announced Upgrade was complete**
* 16:05 - John Confirmed all 4 Sentries were registered and Earning

### Root Cause Analysis <a id="root-cause-analysis"></a>

The view change failed due to a nil pointer issue which was caused by logging on consensus which did not have the required context. See [here](https://github.com/harmony-one/harmony/commit/6ff740ed647d81e9a8e677a26ffad0cfa7873b76) for the fix.

**2. Why did this cause a synching issue?**

Synching all goes of the DNS entry for the shard, in this case api.s0.os.hmny.io

This DNS entry is supported by 5 nodes. In this case four of the nodes were at block height 17061 and one was at block height 17080. This meant that no nodes could sync to the latest block \(17080\).   
****

**3. Why were only five nodes at the latest block height \(17080\)?**

Note only 5 of the 20 nodes were at 17080 the other 15 were at 17061.

All nodes were at 17080, with the last 19 blocks in memory the nil pointer issue caused crashes and those nodes reverted 17061 due to state pruning that lost the last 20 blocks in memory when the program crashed. Thus triggering the synch issues.

**4. Why did the remediation steps fail to solve the problem?**

Reverting to a lower block height \(17061\) rather than the latest \(17080\) left us unable to reach consensus and move forward. Lower block has no required cross-link data to advance the consensus as other shards not impacted had assumed the cross-link to be working.  
****

**5. Why did we not immediately do a hard refresh when reverting?**

Release processes are evolving as our evaluation of our impact to our customers. It may be worthwhile moving straight to a hard refresh when reverting the code base, as we are currently still doing this with other releases. The other option is for more detailed reversion procedures to be developed including tooling for snapshotting all the db’s before beginning each upgrade as well as tooling for reverting to this state.  


### Questions to ask <a id="questions-to-ask"></a>

‌

**1. How was the problem reported? How long did it take to respond to the issue? How could we cut that time in half?**‌

The problem was reported as part of the teams monitoring of the rollout, within 3 minutes of it occurring we were working on a resolution and within 30 minutes we had begun a rollback to the last stable version released.

**2. How long did it take to mitigate the issue? How could we cut that time in half?**‌

It took us 3.5 hours to bring OSTN back up. Performing a hard refresh as part of reverting would have dramatically sped up the process. Also in the remediation stages two mistakes were made the first of which was choosing the lower block height db’s as this would ultimately prevent the ability to gain consensus. The second of which was not backing up those db’s in case of reversion. Finally a db-synch tool would have been useful.

**3. Are there any pending items that can help prevent this issue? If so, why wasn't it prioritized?**‌

Testing of rolling upgrades in STN could have helped prevent the issue in OSTN. Also clearer understanding of remediation practices for the DNS synching issue would have helped. Also an overall review of voting power and consensus and DNS and synching could prevent this moving forward.

**4. Can this issue be detected in a test environment? If not, why?**‌

The issue itself could have been highlighted on STN however it had not gone through an upgrade process and therefore had not triggered a view change. As OSTN is still a testnet for us, we had taken the risk of not imposing too many testing processes before we do a rolling upgrade on OSTN, moving forward we shall test in STN prior to an OSTN release.

### 5 Whys? <a id="5-whys"></a>

**a. Why did this cause a synching issue?**

Synching all goes of the DNS entry for the shard, in this case api.s0.os.hmny.io

This DNS entry is supported by 5 nodes. In this case four of the nodes were at block height 17061 and one was at block height 17080. This meant that no nodes could sync to the latest block \(17080\).   
****

**b. Why were only five nodes at the latest block height \(17080\)?**

Note only 5 of the 20 nodes were at 17080 the other 15 were at 17061.

All nodes were at 17080, with the last 19 blocks in memory the nil pointer issue caused crashes and those nodes reverted 17061 due to state pruning that lost the last 20 blocks in memory when the program crashed. Thus triggering the synch issues.

**c. Why did the remediation steps fail to solve the problem?**

Reverting to a lower block height \(17061\) rather than the latest \(17080\) left us unable to reach consensus and move forward. Lower block has no required cross-link data to advance the consensus as other shards not impacted had assumed the cross-link to be working.  
****

**d. Why did we not immediately do a hard refresh when reverting?**

Release processes are evolving as our evaluation of our impact to our customers. It may be worthwhile moving straight to a hard refresh when reverting the code base, as we are currently still doing this with other releases. The other option is for more detailed reversion procedures to be developed including tooling for snapshotting all the db’s before beginning each upgrade as well as tooling for reverting to this state.  
‌

### Action Items <a id="action-items"></a>

| Category | Description | Owner | Tracker |
| :--- | :--- | :--- | :--- |
| Corrective | ​Fix View Change Issue | ​rongjian@harmony.one | ​[Complete](https://github.com/harmony-one/harmony/commit/6ff740ed647d81e9a8e677a26ffad0cfa7873b76) |
| Preventive | ​Ensure PTN goes through upgrade process before OSTN moving forward | ​john@harmony.one | ​In Progress |
| Preventive | Document Reversion Practice, DB backup | john@harmony.one | In Progress |
| Preventive | Review voting power needed for consensus and it’s impact to synching when nodes supporting DNS are of different values | john@harmony.one | Complete |
| Preventive | Monitoring - Trigger an alert when nodes become out of synch | john@harmony.one | Complete |

