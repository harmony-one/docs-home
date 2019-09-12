---
description: GetBalance returns balance of a given address.
---

# hmy\_getBalance

**HTTP Request Endpoints**

| Chains | URLs |
| :--- | :--- |
| mainnet | TBD |
| betaNet | http://l0.b.hmny.io:9500 |
| local | http://localhost:9500 |

**Arguments**

| Request Data Object | Example |
| :--- | :--- |
| jsonrpc | "2.0" |
| method | "hmy\_getBalance" |
| params | \["0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", "latest"\] |
| id | "1" |

**Transaction Parameters**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter</b>
      </th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">address</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">
        <p>Address represents the 20 byte address of a Harmony account.</p>
        <p>Example</p>
        <p><code>0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">
        <p>Example</p>
        <p><code>latest</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>**Result Parameters**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter</b>
      </th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Balance</td>
      <td style="text-align:left">*hexutil.Big</td>
      <td style="text-align:left">
        <p>Example</p>
        <p><code>0x6046f35fca29af800</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>**Sample Curl Request**

```text
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "hmy_getBalance",
    "params": [
        "0xD7Ff41CA29306122185A07d04293DdB35F24Cf2d", 
        "latest"
        ]
}' -H "Content-Type: application/json" -X POST "http://s0.b.hmny.io:9500"
```

**Sample Curl Response**

```text
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x6046f35fca29af800"
}
```

