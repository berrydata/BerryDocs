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

./BerryMiner mine
```

Before user can run mine command, user should do config setting for running.

## Run with Docker

Coming soon

## Configuration reference

BerryMiner commands and config file options are as the following:

**Required Flags**

* `--config` \(path to your config file.\)

BerryMiner **Commands**

* `--logConfig` \(location of logging config file; default path is current directory\)
* `mine` \(indicates to run the miner\)
* `mine -r` \(indicates to mine utilizing a remote server\)
* `dataserver` \(indicates to run the dataServer \(no mining\)\)
* `transfer` \(AMOUNT\) \(TO ADDRESS\) \(indicates transfer, toAddress is ETH/BSC address and amount is number of Tributes \(eg. transfer 10 0xea... \(this transfers 10 tokens\)\)\)
* `approve` \(AMOUNT\) \(TO ADDRESS\) \(amount to approve the to address to send this amount of tokens
* `stake deposit` \(indicates to deposit tokens in the contract\)
* `stake request` \(indicates you wish to withdraw your stake\)
* `stake withdraw` \(withdraws your stake, run 1 week after request\)
* `stake status` \(shows your staking balance\)
* `balance` \(shows your balance\)

**.env file options, optional:**

* `NODE_URL` \(required\) - node URL \(e.g [https://mainnet.infura.io/bbbb](https://mainnet.infura.io/bbbb) or [https://localhost:8545](https://localhost:8545) if own node\)
* `ETH_PRIVATE_KEY` \(required\) - privateKey for your address
* `$PSR$_KEY` - API key for getting a specific indexes.json api \(required if you use authenticated API's\)

**Config file options:**

* `contractAddress` \(required\) - address of Berry Contract
* `databaseURL` \(required\) - where you are reading from for the server database \(if hosted\)
* `nodeURL` \(optional\) - When you connect to Ethereum Node. It can be set here or in `.env` file
* `publicAddress` \(required\) - public address for your miner \(note, no 0x\)
* `ethClientTimeout` \(required\) - timeout for making requests from your node
* `trackerCycle` \(required\) - how often your database updates \(in seconds\)
* `trackers` \(required\) - which pieces of the database you update
* `dbFile` \(required\) - where you want to store your local database \(if self-hosting\)
* `serverHost` \(required\) - location to host server
* `serverWhitelist` \(required\) - whitelists which publicAddress can access the data server
* `fetchTimeout` - timeout for requesting data from an API
* `requestData` - sets wether your miner request data if challenge is 0.  If yes, then you will addTip\(\) to this number.  Enter a uint number representing request id to be requested \(e.g. 2\)
* `requestDataInterval` - min frequency at which to request data at \(in seconds, default 30\)
* `gasMultiplier` - Multiplies the submitted gasPrice \(e.g. 2 will double gas costs\)
* `gasMax` - a max for the gas price in gwei \(note: this max comes BEFORE the gas multiplier.  So a max gas cost of 10 gwei, can have gas prices up to 20 if gasMultiplier is 2\)
* `heartbeat` - an integer that controls how frequently the miner process should report the hashrate \(larger is less frequent, try 1000000 to start\)
* `numProcessors` - an integer number of CPU cores/threads to use for mining. \(cpu mining is disabled if there is a suitable GPU is found
* `disputeTimeDelta` - how far back to store values for min/max range - default 5 \(in minutes\)
* `disputeThreshold` - percentage of acceptable range outside min/max for dispute checking - default
* `psrFolder` - folder location holding your psr.json file, default working directory
* `privateKey` - private key for miner node to sign transaction, without prefix 0x



#### LogConfig file options

The logging.config file consists of two fields: \* component \* level

The component is the package.component combination.

E.G. the Runner component in the tracker package would be: tracker.Runner

To turn on logging, add the component and the according level. Note the default level is "INFO", so to turn down the number of logs, enter "WARN" or "ERROR"

DEBUG - logs everything in INFO and additional developer logs

INFO - logs most information about the mining operation

WARN - logs all warnings and errors

ERROR - logs only serious errors


