# Data feed IDs

## The Tellor system is a way to push data on-chain.  The **pieces of data that get pushed on-chain are specified off-chain in the submitter code.**

{% hint style="info" %}
Note that each Data ID corresponds to a specific data point. Example: Data ID 4 is BTC/USD in a 24 Hour Time Weighted Average.
{% endhint %}

The Tellor mining system is set up to pull data to generate these values to submit on-chain once a correct nonce is mined. These specific APIs are just suggestions. The system is not guaranteed to work for everyone. It is up to the consensus of the Tellor token holders to determine what a correct value is. In our example, Data ID 4 is BTC/USD. If the APIs all go down, it is the responsibility of the miner to still submit a valid BTC/USD price. If they do not, they risk being disputed and slashed.

