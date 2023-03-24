# pokeMedian.sh

In order to work these script
- ETH_FROM should be set
- private keys of signers should be imported using `ethsign import`
- ETH_PASSWORD should point to valid password file. 
- ETH_GAS=30000000
- ETH_KEYSTORE=/data/helper-scripts/signers/keystore


This script will sign pricing data and call median.poke
- ./pokeMedian.sh $VAL_ETH ETHUSD "1667474316\n1667474316\n1667474316" "500\n1000\n1500"
- ./pokeMedian.sh $VAL_BTC BTCUSD "1667474316\n1667474316\n1667474316" "5000\n10000\n15000"


# setOSMPrice.sh

This script will sign pricing data and call median.poke, then call MegaPoker.poke and then wait for OSM_DEALY after that call PIP.poke
- ./setOSMPrice.sh $VAL_ETH $PIP_ETH ETHUSD
- ./setOSMPrice.sh $VAL_BTC $PIP_BTC BTCUSD


# cronjobs

## goerli

- */15 * * * * /data/helper-scripts/pricing/setOSMPrice.sh 0x587A22d89f24F60ea472212185E023a0eE8938F6 0x35e2f21670C8D0cb972376671032F7c3bd60A497 ETHUSD >> ~/OSM_PRICE_UPDATE_ETH.log 2>&1
- */30 * * * * /data/helper-scripts/pricing/setOSMPrice.sh 0x04946431bF40045cFf3Dbfd60A4d64454D08768a 0xcD9cEA4Cfb76d7BA6acD35866E1da212F5488eA5 BTCUSD >> ~/OSM_PRICE_UPDATE_BTC.log 2>&1