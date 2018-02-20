# pymsl
Python library for interacting with the Netflix MSL API

# Usage

### Basic Usage

```python
>>> import pymsl
>>> user_auth_data = {
...     'scheme': 'EMAIL_PASSWORD',
...     'authdata': {
...         'email': email,
...         'password': password
...     }
... }
>>> client = pymsl.MslClient(user_auth_data)
>>> client.load_manifest([80092521])
{'success': True, ...
```

### Custom Kwargs

`pymsl.MslClient()` takes additional kwargs as well to override the defaults; the only required arg for initialization is user_auth_data:

```python
>>> pymsl.MslClient(
...     user_auth_data,
...     esn=CUSTOM_ESN, # default is NFCDCH-02-[random device ID]
...     drm_system=CUSTOM_DRM_SYSTEM, # default is 'widevine', you can use 'playready', 'fps', etc.
...     profiles=LIST_OF_PROFILES, # default is ['playready-h264mpl30-dash', 'playready-h264mpl31-dash', 'playready-h264mpl40-dash', 'heaac-2-dash', 'simplesdh', 'nflx-cmisc', 'BIF240', 'BIF320']
...     keypair=CUSTOM_CRYPTODOME_RSA_KEYPAIR, # default is a random 2048-bit keypair
...     message_id=CUSTOM_MESSAGE_ID, # default is a random integer between 0 and 2^52
...     languages=LIST_OF_LANGUAGES # default is ['en_US']
... )
```

### Methods

`load_manifest(viewable_ids)` returns a manifest as a dict for the list of viewable_ids supplied
`get_license(challenges)` returns licenses as a dict for the list of challenges supplied (not implemented yet)

# To-Do

- [ ] Implement license acquisition
- [ ] Clean up chunked payload parsing
