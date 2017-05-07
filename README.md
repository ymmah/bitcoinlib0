# bitcoinlib
Bitcoin and other Cryptocurrencies Library for Python

[![Build Status](https://travis-ci.org/1200wd/bitcoinlib.svg?branch=master)](https://travis-ci.org/1200wd/bitcoinlib)
[![PyPI](https://img.shields.io/pypi/v/bitcoinlib.svg)](https://pypi.python.org/pypi/bitcoinlib/)
[![Documentation Status](https://readthedocs.org/projects/bitcoinlib/badge/?version=latest)](http://bitcoinlib.readthedocs.io/en/latest/?badge=latest)


## Documentation

Can be found at http://bitcoinlib.readthedocs.io/


## Features

#### Mnemonic Keys
Allows you to use easy to remember passphrases consisting of a number of words to store private keys (BIP0039).
You can password protect this passphrase (BIP0038), and use the HD Wallet structure to generate a almost infinite 
number of new private keys and bitcoin addresses (BIP0043 and BIP0044).

#### Wallet
The bitcoinlibrary contains a wallet implementation using sqlalchemy and sqllite3 to import, create and manage 
keys in a Hierarchical Deterministic Way.

Example: Create wallet and generate new key to receive bitcoins

```
>>> from bitcoinlib.wallets import HDWallet
>>> w = HDWallet.create('Wallet1')
>>> w
<HDWallet (id=1, name=Wallet1, network=bitcoin)>
>>> key1 = w.new_key()
>>> key1
<HDWalletKey (name=Key 0, wif=xprvA4BoA5WSjsqAsRZPRjZnMg5LViLosJT83DWzURDtEUeo2iYcsctbvffqsL9RdfzFWd4Xiy6UDQjr878UEXVEfyfenNcPpJXC6HZKGW7Kozc, path=m/44'/0'/0'/0/0)>
>>> key1.address
'1Fo7STj6LdRhUuD1AiEsHpH65pXzraGJ9j'
```

When your wallet received a payment and has unspent transaction outputs, you can send bitcoins easily.
If succesfull a transaction ID is returned

```
>>> w.send_to('12ooWd8Xag7hsgP9PBPnmyGe36VeUrpMSH', 100000)
'b7feea5e7c79d4f6f343b5ca28fa2a1fcacfe9a2b7f44f3d2fd8d6c2d82c4078'
```

#### Service providers
Communicates with pools of bitcoin service providers to retreive transaction, address, blockchain information. 
To push a transaction to the network. To determine optimal service fee for a transaction. Or to update your
wallet's balance.

#### Implements the following Bitcoin Improvement Proposals
- Hierarchical Deterministic Wallets (BIP0032)
- Passphrase-protected private key (BIP0038)
- Mnemonic code for generating deterministic keys (BIP0039)
- Purpose Field for Deterministic Wallets (BIP0043)
- Multi-Account Hierarchy for Deterministic Wallets (BIP0044)


## Installation

Install with pip

    pip install bitcoinlib
   

#### Package dependencies

Required Python Packages, are automatically installed upon installing bitcoinlib:
- ecdsa
- pbkdf2
- pycrypto
- scrypt
- sqlalchemy

#### Python development packages
    sudo apt install python-dev python3-dev

#### To install OpenSSL development package on Debian, Ubuntu or their derivatives:
    sudo apt install libssl-dev

#### To install OpenSSL development package on Fedora, CentOS or RHEL:
    sudo yum install openssl-devel


## References

- https://pypi.python.org/pypi/bitcoinlib/
- https://github.com/1200wd/bitcoinlib