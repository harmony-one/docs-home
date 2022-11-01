# Help

## How to find out what's with my bridge operation?
You can find the operation details on your operation page. 
It's the page you see when you perform the operation on 
<a href="https://bridge.harmony.one/" target="_blank">
the LayerZero bridge site.
</a>
Every bridge operation is associated with a unique operation id, which is shown on the page.
You can find links to transactions of the operation steps and the status of each step.
<br/>
Also, you can always find your operation in the <a href="https://bridge.harmony.one/explorer"> bridge operation explorer.</a>
Use "My transaction" option to see only operations for your connected Metamsk account.

## Transaction pending for too long
If your transaction is pending for too long, you can manage it via your
wallet. We can’t make it faster or cancel it. If the transaction is on
Harmony side, make sure you use 
<a href="https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet/adding-harmony">
recommended settings
</a> 
for Harmony network.

## Operation in progress for too long
Normally it takes less than 20 minutes per each step of the bridge operation. 
Delays are also possible, but they won't affect your funds.
<br />
If your operation is in progress for <b>more than an
hour</b>, you can fill in the <a href="https://bridge.harmony.one/support"> support form </a> and include you problem description. 
Note that your request will be ignored if you send it earlier.

## Operation status is success, but I can’t find my tokens
Bridge does not swap tokens, it only provides wrapped tokens. For the
token that you bridged, you have received wrapped token to your account.
To find out which one, you can refer to [this page](./FAQ/token-address.md).
<br />
<ul>
Note that:
<li>
Bridge is not a swap, and you won't receive ONE if you weren't
bridging ONE token.
</li>
<li>
A token address is never the same in the different networks, even
when a symbol is the same.
</li>
</ul>
<br />
If you don't see that token in your account, and add it to your wallet to see the correct balance as shown 
<a href="https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet/adding-custom-harmony-tokens" target="_blank" rel="noreferrer">
here. 
</a>
<br />
If you have problems with finding or adding a token, please ask for
help in community groups.

<br />
<ul>
If you added a token and tokens aren’t shown, check that:
<li> You added a token to the receiver wallet of your operation.</li>
<li>
The receiver address of your operation is correct. If you found out
that you made a mistake in the address, we can’t help you with that.
You can reach your funds only if you have access to the wallet.
</li>
<li>
The receiver wallet is connected to the correct network. For
example, if you bridged tokens to Harmony, you need to be connected
to Harmony mainnet.
</li>
<li>
You’ve added a token that you really received. Check the transaction
data.
</li>
<li>
Tokens haven’t been transferred after the bridge. 
</li>
</ul>
<br />
If a correct balance isn’t shown after you added a token, and you have
double-checked everything, fill in the <a href="https://bridge.harmony.one/support"> support form</a> and include you problem description.
It’s required to include a token address you added and a wallet you added it to.

## Bridge error, funds lost
Please fill in the <a href="https://bridge.harmony.one/support"> support form</a> and include you problem description.

## I can’t bridge because of an error
There can be many possible causes. Sometimes the reason is clear from
the error message (for example, low balance, not enough tokens to cover gas).
<br /> Often there is a problem with the wallet connection. Try these
steps to solve it:
<ul>
<li>
Make sure your browser and the wallet extension are updated to the
latest version
</li>
<li> Make sure that your browser doesn’t block pop-up windows.</li>
<li> Try to clear the cache and relogin.</li>
<li>
Check
<a href="https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet/adding-harmony">
here
</a>
if your wallet is set up correctly.
</li>
<li> Try using another browser or/and wallet extension.</li>
<li> If you use a mobile version, try it on the desktop.</li>
</ul>
If you’ve checked your settings, but you still have errors, please share
your problem in the #support or #bridge
<a href="https://discord.com/invite/YJ6kgEZ5ed">Discord</a> channel.

## By mistake sent tokens to an exchange wallet (e.g. Binance exchange)
Unfortunately, your tokens are permanently lost and not recoverable.

## I sent tokens to a wallet that doesn’t support the network I used
If you can’t open your wallet in the network where your tokens were
sent, we can’t assist. You can try to reach a support of the service
that gave you this account.

## By mistake sent tokens to a wrong address or a token address
Unfortunately, we can't help in such case. We don't have access needed
to transfer tokens between accounts.

## I have a question about the LayerZero bridge
You can address your question to Harmony community in Discord or Telegram. Please beware of scammers.
Remember, admins never DM you first.
Please refer to our
<a href="https://docs.harmony.one/home/general/bridges/layerzero-bridge/faq" target="_blank">
FAQ
</a>
first.


