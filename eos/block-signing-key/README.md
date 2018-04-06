# Block Signing Key

Scholar Testnet requests that all Block Producers generate & provide an EOS Public key (which they own the private key and is stored safely).

If none is provided, an EOS key pair will be generated for you and sent via your Keybase account.

## Creating EOS key pair with `cleos`

```
$ cleos create key
Private key: <EOS PRIVATE KEY>
Public key: EOS78uKLgYYSgQHXyJbbjDzXpibChtcYGKmooz8AmyiDhTiaC1Syz
```

Please submit a GitHub Pull Request (PR) to the appropriate [Block Producers YAML config](https://github.com/ScholarTestnet/scholar-block-producers/tree/master/block-producers) and edit `block_signing_key`.

