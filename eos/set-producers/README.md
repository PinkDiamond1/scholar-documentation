# Set Producers

## How I set producers, after initializing the tokens:

#### Step 1: Re-install BIOS contract:

```
cleos set contract eosio \
  contracts/eosio.bios \
  contracts/eosio.bios/eosio.bios.wast \
  contracts/eosio.bios/eosio.bios.abi
```

#### Step 2: Set Producers

Create a `setprods.json` file using the following schema:

```
{
  "version": "12345",
  "producers": [
    {
      "producer_name": "eos.nation",
      "block_signing_key": "EOS78uKLgYYSgQHXyJbbjDzXpibChtcYGKmooz8AmyiDhTiaC1Syz"
    }
  ]
}
```

```
cleos push action eosio setprods ./setprods.json -p eosio@active
```

#### Step 3: Re-install core contracts

```
cleos set contract eosio \
  contracts/eosio.system \
  contracts/eosio.system/eosio.system.wast \
  contracts/eosio.system/eosio.system.abi

cleos set contract eosio \
  contracts/eosio.token \
  contracts/eosio.token/eosio.token.wast \
  contracts/eosio.token/eosio.token.abi
```
