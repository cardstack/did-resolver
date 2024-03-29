# did-resolver

This is a copy of [Typescript DID Resolver](https://www.npmjs.com/package/did-resolver).

## Install

It is available on [PyPi](https://pypi.org/project/did-resolver/)

```
pip install did-resolver
```

## Usage

```python
from did_resolver import Resolver


def get_resolver():
    def resolve(did, _1, _2):
        return {
            "didResolutionMetadata": {"contentType": "application/did+ld+json"},
            "didDocument": {
                "@context": "https://w3id.org/did/v1",
                "id": did,
                "verificationMethod": [
                    {
                        "id": "owner",
                        "controller": "1234",
                        "type": "xyz",
                    },
                ],
            },
            "didDocumentMetadata": {},
        }

    return {"cardstack": resolve}


example_did = "did:cardstack:1pWMyKj3qfgbTtdBuaWSGUeN70913f2bde84cb36"
print(Resolver(get_resolver()).resolve(example_did))
```

## Publish

```
pdm plugin add pdm-publish
pdm publish --password <token>
```
