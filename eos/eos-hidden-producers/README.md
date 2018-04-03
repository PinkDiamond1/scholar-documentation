# Securing your Block Producer Machine

This document aims to provide the technical knowledge and numerous ways you can secure your Block Producer machine.

## 1. Producer behind Firewall

- Setup your Block Producer full node behind a firewall
- Setup a full node for incoming traffic
- Connect your producing node to your listening node
- Only your listening node should be exposed to the public, thus making your producing node "hidden" to others.

## 2. Signing Nodes

Not yet implemented by the EOS.IO Softare, however similar to the `Producer behind Firewall` approach except the listening node would be called your "Signing Node" instead using it's own EOS private key/public key.
