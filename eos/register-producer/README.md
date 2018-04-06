# Register Producer

@Denis Carriere:

Topic: Registering Hardware specification to `eosio.system` contract

@Alex Bourget:

you mean the parameters there ?  it's not necessarily hardware parameters, but staked price per CPU cycle, bandwidth, etc.. there are two handfuls parameters that BPs need to understand and "vote" for.. or adjust on the network.. this requires a deep understanding of the resources allocation and pricing system, etc..

@Denis Carriere:
There a lot of `eosio_parameter` you can configure, would it be each BP that would need to configure these parameters?

https://github.com/EOSIO/eos/blob/master/contracts/eosio.system/eosio.system.abi#L87-L113

@Alex Bourget:
When you regproducer, you need to provide a value for all of them, and the "median" of all those values is what is used as effective parameters on the blockchain for that 63 seconds round...

See: https://github.com/EOSIO/eos/blob/master/contracts/eosio.system/voting.hpp#L245-L361
