## Status API

This is our API status endpoint.

### Get Status

Check the status of the Biocaching API.

```endpoint
GET http://api.biocaching.com/
```

#### Example request

```curl
$ curl http://api.biocaching.com/
```

#### Example responses

```json
{
  "message": "This is the Biocaching API, ES is up and running"
}
```

```json
{
  "message": "This is the Biocaching API, ES is down..."
}
```
