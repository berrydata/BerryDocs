---
description: Sample project UsingBerry
---

# Using Berry Sample

**The Berry oracle** is a decentralized oracle on Binance Smart Chain. It provides an option for contracts to securely interact with and obtain data from off-chain.

Quick references are included below:

**Implement Berry into your project** This repo already includes the [usingBerry](https://github.com/berrydata/UsingBerry) package.

### How to use

**1. Clone the project and install dependencies**

```text
git clone git@github.com:berrydata/SampleUsingBerry.git
npm install 
```

**2. How to Use**

Just Inherit the UsingBerry contract, passing the Berry address as a constructor argument:

Here's an example

```text
contract BtcPriceContract is UsingBerry {

  //This Contract now have access to all functions on UsingBerry

  uint256 btcPrice;
  uint256 btcRequetId = 1;

  constructor(address payable _berryAddress) UsingBerry(_berryAddress) public {}

  function setBtcPrice() public {
    bool _didGet;
    uint _timestamp;
    uint _value;

    (_didGet, btcPrice, _timestamp) = getCurrentValue(btcRequetId);
  }
}
```

**Addresses:**

BSC Mainnet: [\`\`](https://etherscan.io/address/)

**3. The sample contract SampleUsingBerry have access to the following Berry functions:**

```text
    /**
    * @dev Retreive value from oracle based on requestId/timestamp
    * @param _requestId being requested
    * @param _timestamp to retreive data/value from
    * @return uint value for requestId/timestamp submitted
    */
    function retrieveData(uint256 _requestId, uint256 _timestamp) public view returns(uint256);

    /**
    * @dev Gets if the mined value for the specified requestId/_timestamp is currently under dispute
    * @param _requestId to looku p
    * @param _timestamp is the timestamp to look up miners for
    * @return bool true if requestId/timestamp is under dispute
    */
    function isInDispute(uint256 _requestId, uint256 _timestamp) public view returns(bool);

    /**
    * @dev Counts the number of values that have been submited for the request
    * @param _requestId the requestId to look up
    * @return uint count of the number of values received for the requestId
    */
    function getNewValueCountbyRequestId(uint256 _requestId) public view returns(uint);

    /**
    * @dev Gets the timestamp for the value based on their index
    * @param _requestId is the requestId to look up
    * @param _index is the value index to look up
    * @return uint timestamp
    */
    function getTimestampbyRequestIDandIndex(uint256 _requestId, uint256 _index) public view returns(uint256);

    /**
    * @dev Allows the user to get the latest value for the requestId specified
    * @param _requestId is the requestId to look up the value for
    * @return bool true if it is able to retreive a value, the value, and the value's timestamp
    */
    function getCurrentValue(uint256 _requestId) public view returns (bool ifRetrieve, uint256 value, uint256 _timestampRetrieved);

    /**
    * @dev Allows the user to get the first value for the requestId before the specified timestamp
    * @param _requestId is the requestId to look up the value for
    * @param _timestamp before which to search for first verified value
    * @return bool true if it is able to retreive a value, the value, and the value's timestamp
    */
    function getDataBefore(uint256 _requestId, uint256 _timestamp)
        public
        view
        returns (bool _ifRetrieve, uint256 _value, uint256 _timestampRetrieved);
```

**5. To run tests:**

```text
npm run test
```

**6. Migrations:**

Just run truffle migrate with the desired Network

```text
truffle migrate
```

