# zte config utility

The core of the decoding work is taken from a [pastebin](https://pastebin.com/GGxbngtK) dump by 'Felis-Sapien'.

Creates byte-perfect binaries for the limited number of `config.bin` that have been tested.

## Quickstart

Clone the repo and run `python3 setup.py install --user`.

## Examples

### Decode/Encode a type-2, version 2 `config.bin`
```sh
$ python3 examples/decode.py resources/ZXHN_H298N.bin resources/ZXHN_H298N.xml --key 'Wj'
$ python3 examples/encode.py resources/ZXHN_H298N.xml resources/ZXHN_H298N.NEW.bin --key 'Wj' --signature 'ZXHN H298N'
$ md5sum resources/ZXHN_H298N.bin resources/ZXHN_H298N.NEW.bin
8529c1e3d4e3018db508a3b5b5b574cc  resources/ZXHN_H298N.bin
8529c1e3d4e3018db508a3b5b5b574cc  resources/ZXHN_H298N.NEW.bin
```

### Decode/Encode a type-2, version 1 `config.bin`
```sh
$ python3 examples/decode.py resources/ZXHN_H108N_V2.5.bin resources/ZXHN_H108N_V2.5.xml --key 'GrWM2Hz&LTvz&f^5'
$ python3 examples/encode.py resources/ZXHN_H108N_V2.5.xml resources/ZXHN_H108N_V2.5.NEW.bin --key 'GrWM2Hz&LTvz&f^5' --signature 'ZXHN H108N V2.5' --version 1
$ md5sum resources/ZXHN_H108N_V2.5.bin resources/ZXHN_H108N_V2.5.NEW.bin
5dbb537bb8a5bfa51f9bc9e2d48f576d  resources/ZXHN_H108N_V2.5.bin
5dbb537bb8a5bfa51f9bc9e2d48f576d  resources/ZXHN_H108N_V2.5.NEW.bin
```

### Decode/Encode a type-0 `config.bin`
```sh
$ python3 examples/decode.py resources/F600W.bin resources/F600W.xml
$ python3 examples/encode.py resources/F600W.xml resources/F600W.NEW.bin --signature F600W --payload-type 0
$ md5sum resources/F600W.bin resources/F600W.NEW.bin
a6ac0e5e04f705b54747c30f80dfd4ba  resources/F600W.bin
a6ac0e5e04f705b54747c30f80dfd4ba  resources/F600W.NEW.bin
```

### Grab 'signature' from a `config.bin`
```sh
$ python3 examples/signature.py resources/ZXHN_H108N_V2.5.bin
ZXHN H108N V2.5
```

## Limitations

The decoder has only been tested against `config.bin` files generated by the following routers:
 - `ZXHN H298N`
 - `ZXHN H108N V2.5`
 - `F600W`

And a `db_default_auto_cfg.xml` file extracted from a firmware for `ZXHN H268N`

It makes a number of assumptions due to this. The encoder has not been tested in the wild. Use at your own risk.

## Requirements

The AES encryption relies on [pycryptodomex](https://pypi.org/project/pycryptodomex/)