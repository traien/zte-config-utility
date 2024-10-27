## Quickstart

Clone the repo and run

```sh
mkdir env
python3 -m venv env
source env/bin/activate
python3 -m pip install xyz
```

**NOTE:** This project has only been tested against **Python 3.7** and higher.

### Decode


```sh
python3 examples/decode.py config.bin resources/config.xml --serial SERIALNO
```

## Encode

```sh
python3 examples/encode.py resources/config.xml resources/config.bin --serial SERIALNO --signature 'ZXHN H298A V1.0'
```

