# Flow of Work

BERRY is an oracle system where parties can request the value of an off-chain data point and miners compete to add this value to an on-chain data-bank, accessible by all dApps on Binance Smart Chain. The inputs to this data-bank are secured by a network of staked miners. BERRY utilizes crypto-economic incentive mechanisms, rewarding honest data submissions by miners and punishing bad actors, through the issuance of BERRY’s governance token, BRY, and a dispute mechanism.

\*\*\*\*1 **Data Request is submitted**: The user submits a query to Berry Data to incentivize miners to choose this query over other submissions. Other users who want the same data pay this data series to further incentivize selection by miners.

\*\*\*\*2 **Miners begin to work**: Miners submit their PoW solution and off-chain data points to the Seer contract. The Berry contract sorts the values as they come in and as soon as five values are received, the official value \(median of the five\) is selected and saved on-chain.

\*\*\*\*3 **Data Feeds are generated and distributed**: Every 2.5 minutes, Berry's smart contract selects the best-funded queries and provides a new challenge for miners to solve.

\*\*\*\*4 **Wrong Data can be disputed**: Anyone holding Berry governance token \(BRY\) can dispute the validity of a mined value by paying a dispute fee. Over the next two days, Berry token holders will vote on the validity of the data point.

## Charge Model

The initial phase of the project \(6 months after launch\) is free of charge for partners to provide on-chain quotes, and as demand increases, the project will consider charging to form a healthy business model to help the project develop better.

