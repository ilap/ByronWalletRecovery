# inspect-keystore

A tool for inspecting the content of a Cardano keystore.

## Installation

```
yarn
```

## Usage

```
yarn inspect-keystore [FILEPATH]
```

## Examples

### No address and legacy address provided
```
yarn inspect-keystore examples/secret.key
```

```json
[
    {
        "encrypted-root-private-key": "root_xsk1...",
        "root-public-key": "root_xvk1fv6wc376lxm7h34akurxyfskg5wqqr59h2quw3y6usm23jal824e3ewvwpyh00g3hv9634d42ud8q4cyewfnf5n6qjzn9645nf5cctg4d3elm",
        "source": "_usKeys",
        "is-empty-passphrase": false,
        "has-valid-encryption": false,
        "encryption-password": ""
    },
    {
        "encrypted-root-private-key": "root_xsk1...",
        "root-public-key": "root_xvk16vm9zdmhx8swt8szxdp954f9w7pvttd2w6x6q4nlg0qudsxpsanw6zj50we5adrjcystzu9gvsp8nqedmuvqq2y87q7pth49juz5ytg5cxpzz",
        "source": "_usKeys",
        "is-empty-passphrase": true,
        "has-valid-encryption": true,
        "encryption-password": ""
    },
    {
        "encrypted-root-private-key": "root_xsk1...",
        "root-public-key": "root_xvk160gu7m79v4rkc9ejdwhtmh8nr30rgzd6d9aehuz2ckyvkkvx3s3dqslqydarhghtze732pxaj0mc3lz2wfgr5fsu7vu26ljvlzph4lc292vae",
        "source": "_usKeys",
        "is-empty-passphrase": true,
        "has-valid-encryption": true,
        "encryption-password": ""
    },
    {
        "encrypted-root-private-key": "root_xsk1...",
        "root-public-key": "root_xvk122hdyt8065l2046mtqz2m42wv57zrcpll47qrju0dspn7lfc8nqjwprpfrvf5xpgka4ak344dah7cpknrdd5ztwx326ttlazgx88arg9pcjqy",
        "source": "_usKeys",
        "is-empty-passphrase": false,
        "has-valid-encryption": false,
        "encryption-password": ""
    }
]
```

### No password but legacy address provided

``` bash
yarn inspect-keystore  examples/iog_secret.key "" "DdzFFzCqrht3HPYUiN4jnDyXBaWTMdikTZxdnojP3kxHBuvFB7QjbaYriFFfPLqHY622aCXAqKrq34xNNe1rvkW4uAGFUDtDrX4yQRaR"
# Or on macOS or Windows, you must change working directory to
# inspect-keystore directory/folder.

node index.js examples/iog_secret.key "" "DdzFFzCqrht3HPYUiN4jnDyXBaWTMdikTZxdnojP3kxHBuvFB7QjbaYriFFfPLqHY622aCXAqKrq34xNNe1rvkW4uAGFUDtDrX4yQRaR"
```

``` json
[
    {
        "encrypted-root-private-key": "root_xsk1...",
        "root-public-key": "root_xvk1jmuul53lucc9sat9v0v44eez0tqs6d7yhky8xwsxggx8vcvaww8artrqv22780tsa20k33ud2pdd2z5lrhjc3pzujcsc5m5fjqaccug2qv093",
        "source": "_usKeys",
        "is-empty-passphrase": true,
        "has-valid-encryption": true,
        "encryption-password": "",
        "is-wallet-address": true,
        "address-derivation-path": [
            2147483648,
            3730959219
        ],
        "is-address-from-decrypted-key": true
    }
]
```

## TODO

- [ ] Also extract `_usPrimKey` from the keystore and understand what it was used for. 
      This is definitely not set in newer wallets, but it seems that a few old wallets 
      did carry a 'PrimKey' which usage is relatively undefined at this stage.
