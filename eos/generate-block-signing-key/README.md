# Generate Block Signing Key

Scholar Testnet requires all Block Producers to generate & provide an EOS Public key, this key will be required for the Block Producers to generate blocks on the Scholar Testnet.

> Make sure you store your EOS private key in a safe & secure location.

If no EOS public key is provided, an EOS key pair can be generated for you and sent via your Keybase account.

## Creating EOS key pair with `cleos`

```
$ cleos create key
Private key: <EOS PRIVATE KEY>
Public key: EOS78uKLgYYSgQHXyJbbjDzXpibChtcYGKmooz8AmyiDhTiaC1Syz
```

Once your EOS key pairs are generated, you can submit the EOS Public key via a GitHub Pull Request (PR) to the [Block Producers YAML configs](https://github.com/ScholarTestnet/scholar-block-producers/tree/master/block-producers) and edit the `block_signing_key` configuration. 
