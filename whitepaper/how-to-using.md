---
description: Here are the nuts and bolts for using Berry to get price
---

# How to Using

Berry Data have publish `npm` package, name `usingberry`, user can you this package to get latest price. Just inherit the `UsingBerry` contract, passing the Berry Master address a constructor argument. Here is an example:

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

## Address:

BSC Testnet: `0x8af6EAbf2b4dA47FD9640CC0EcE16e52BEe4728f`

BSC Mainnet: 

## Pre Set Request ID

1, BTC/USD

2, ETH/USD

3, LINK/USD

4, LTC/USD

5, XRP/USD

6, BNB/USD





