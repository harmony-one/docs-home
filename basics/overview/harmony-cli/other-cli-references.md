# Other CLI references

## Generate Markdown documentation

if you want a full list of commands the `hmy` tool knows in markdown format, please run the following command:

```bash
./hmy docs
```

Then in the same directory, `hmy` creates a directory named `hmy-docs` in which you can find all markdown files for the commands and subcommands.

## Delete one account

Deletion of a one account is possible by issuing the below command

```bash
 ./hmy keys remove [ACCOUNT-NAME]
```

{% hint style="danger" %}
Be sure to have saved your private keys before if you had fund in that account. Deleting the account without backing it up means you'll lose it forever.
{% endhint %}

