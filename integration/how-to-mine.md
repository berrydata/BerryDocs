---
description: 'Here are the nuts and bolts for mine, and provide price for Berry Oracle'
---

# How to Mine

## Get Miner

Now Berry Data official release version only support Ubuntu. You should build yourself by BerryMiner source code if you use other os system.

Other configuration description including `dataserver`,  `mine remote` will coming soon.

## Run CLI

Download BerryMiner binary file from [BerryMiner Github](https://github.com/berrydata/BerryMiner/releases), get latest miner.

Extract tar file in your server, then you should do config as follow.

#### How to start

Firstly you should config your account in `config.json`

Please input your account address and private key in `config.json`, both are not with prefix `0x`

If you want to use GPU, you should set `useGPU` to true in  `config.json`, and also you should check your  system has `libOpenCL` library,  you can install it by this command

```bash
sudo apt install ocl-icd-opencl-dev
```

#### Stake 1000 BRY

Then please confirm that your account have 1000 BRY and some BNB for mining fee.

You can use follow command to check your balance:

```bash
./BerryMiner balance
```

Its output should  as follow

```bash
0xe010aC6e0248790e08F42d5F697160DEDf97E024
      0.91 ETH
   1034.73 BRY
```

Now you can start stake 1000 BRY for mining, by this command

```bash
./BerryMiner stake deposit
```

You can use this command to check your stake status

```bash
./BerryMiner stake status
```

Its output should as follow

```bash
Staked in good standing since 2021-03-09 00:00:00 +0000 UTC
```

#### Start Mining

You can use this command to start mining

```bash
nohup ./BerryMiner mine &
```

## Configuration reference

BerryMiner commands and config file options are as the following:

**Required Flags**

* `--config` \(path to your config file, default it is in same fold of `BerryMiner`\)

BerryMiner **Commands**

* `--logConfig` \(location of logging config file; default path is current directory\)
* `mine` \(indicates to run the miner\)
* `mine -r` \(indicates to mine utilizing a remote server\)
* `dataserver` \(indicates to run the dataServer \(no mining\)\)
* `transfer` \(AMOUNT\) \(TO ADDRESS\) \(indicates transfer, toAddress is BSC address and the amount is number of Tributes \(eg. transfer 10 0xea... \(this transfers 10 tokens\)\)\)
* `approve` \(AMOUNT\) \(TO ADDRESS\) \(amount to approve the to address to send this amount of tokens
* `stake deposit` \(indicates to deposit tokens in the contract\)
* `stake request` \(indicates you wish to withdraw your stake\)
* `stake withdraw` \(withdraws your stake, run 1 week after request\)
* `stake status` \(shows your staking balance\)
* `balance` \(shows your balance\)

**Template Config file:**

```bash
{
    "contractAddress": "0xf859Bf77cBe8699013d6Dbc7C2b926Aaf307F830",
    "nodeURL": "https://bsc-dataseed1.binance.org",
    "publicAddress": "your_account_address_no_prefix_0x",
    "privateKey": "your_account_private_key_no_prefix_0x",
    "serverHost": "localhost",
    "serverPort": 5001,
    "ethClientTimeout": 3000,
    "trackerCycle": 10,
    "requestData":0,
    "gasMultiplier": 1,
    "gasMax":30,
    "useGPU":false,
    "trackers": [
        "balance",
        "disputeStatus",
        "gas",
        "tributeBalance",
        "indexers"
    ],
    "dbFile": "berryDB"
}
```

**Config file options:**

* `contractAddress` \(required\) - address of Berry Contract
* `nodeURL` \(required\) - When you connect to BSC Node.
* `publicAddress` \(required\) - public address for your miner \(note, no 0x\)
* `privateKey` - private key for miner node to sign transaction, without prefix 0x
* `ethClientTimeout` \(required\) - timeout for making requests from your node
* `trackerCycle` \(required\) - how often your database updates \(in seconds\)
* `trackers` \(required\) - which pieces of the database you update
* `dbFile` \(required\) - where you want to store your local database \(if self-hosting\)
* `serverHost` \(required\) - location to host server
* `serverWhitelist` \(required\) - whitelists which publicAddress can access the data server
* `fetchTimeout` - timeout for requesting data from an API
* `requestData` - sets wether your miner request data if the challenge is 0.  If yes, then you will addTip\(\) to this number.  Enter a uint number representing request id to be requested
* `requestDataInterval` - min frequency at which to request data at \(in seconds, default 30\)
* `gasMultiplier` - Multiplies the submitted gasPrice
* `gasMax` - a max for the gas price in gwei \(note: this max comes BEFORE the gas multiplier.  So a max gas cost of 10 gwei, can have gas prices up to 20 if gasMultiplier is 2\)
* `heartbeat` - an integer that controls how frequently the miner process should report the hashrate \(larger is less frequent, try 1000000 to start\)
* `numProcessors` - an integer number of CPU cores/threads to use for mining. \(cpu mining is disabled if there is a suitable GPU is found
* `disputeTimeDelta` - how far back to store values for min/max range - default 5 \(in minutes\)
* `disputeThreshold` - percentage of acceptable range outside min/max for dispute checking - default



#### LogConfig file options

The logging.config file consists of two fields: \* component \* level

The component is the package.component combination.

E.G. the Runner component in the tracker package would be: tracker.Runner

To turn on logging, add the component and the according level. Note the default level is "INFO", so to turn down the number of logs, enter "WARN" or "ERROR"

DEBUG - logs everything in INFO and additional developer logs

INFO - logs most information about the mining operation

WARN - logs all warnings and errors

ERROR - logs only serious errors



