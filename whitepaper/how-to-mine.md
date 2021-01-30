---
description: Here are the nuts and bolts for mine
---

# How to Mine

## Get Miner

Now, Berry Data support Linux and MacOS for mining OS. User can use CLI or use Docker to run miner.



## Run CLI

```bash
git clone https://github.com/berrydata/BerryMiner
./release_build.sh
```

After build user will get `BerryMiner`,  Then user should config for run mining

### Configuration

```bash
{
    "contractAddress": "0x7DdC408C0Cd13D3543156AE2bc5772C56E91AA0f",
    "nodeURL": "http://localhost:8545",
    "publicAddress": "xxx",
    "privateKey": "xxx",
    "serverHost": "localhost",
    "serverPort": 5005,
    "ethClientTimeout": 3000,
    "trackerCycle": 10,
    "requestData":0,
    "gasMultiplier": 1,
    "gasMax":10,
    "useGPU":false,
    "trackers": [
        "balance",
        "disputeStatus",
        "gas",
        "tributeBalance",
        "indexers"
    ],
    "dbFile": "berryDB5"
}

```

contract address is master address for Berry Data

nodeURL is Ethereum endpoint





## Run with Docker

