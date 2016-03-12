## Users

Access user data and settings.

### Sign in

Authorize a user and get a access token that can be used to invoke future API services.

```endpoint
POST http://api.biocaching.com/users/sign_in
```

#### Request headers

```http
Content-Type: application/json
Accept: application/json
```

#### Example request body

```json
{
  "user": {
    "email": "<EMAIL>",
    "password": "<PASSWORD>"
  }
}
```

#### Example request

```curl
$ curl  -H 'Content-Type: application/json' -H 'Accept: application/json' \
  -X POST "http://api.biocaching.com:82/users/sign_in" \
  -d '{"user" : { "email" : "<EMAIL>", "password" : "<PASSWORD>"}}' \
```

#### Example response

```json
{
  "id": 3,
  "email": "albin@biocaching.com",
  "created_at": "2016-02-16T14:05:14.000Z",
  "updated_at": "2016-03-07T20:11:50.556Z",
  "authentication_token": "fBBYhbnVufGH1pKxv895",
  "firstname": "Albin",
  "lastname": "Larsson",
  "displayname": "Abbe"
}
```

> 401

```json
{
  "error": "Invalid email or password."
}
```


### Get Settings

Get user settings.

```endpoint
GET http://api.biocaching.com/settings
```

#### Request headers

```http
Content-Type: application/json
Accept: application/json
X-User-Email: <EMAIL>
X-User-Token: <TOKEN>
```

#### Example request

```curl
$ curl  -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'X-User-Email: <EMAIL>' -H 'X-User-Token: <TOKEN>' \
  -X GET "http://api.biocaching.com:82/settings" \
```

### Update Settings

```endpoint
PUT http://api.biocaching.com/settings
```

#### Request headers

```http
Content-Type: application/json
Accept: application/json
X-User-Email: <EMAIL>
X-User-Token: <TOKEN>
```

#### Example request body

```json
{
  "settings": {
    "collection_id": 1,
    "languages": "eng",
    "region": "nor"
  }
}
```

JSON Proprieties | Description
---|---
`collection_id` | (optional) a collection to use as a filter for taxa search.
`languages` | (optional) a comma separated list of ISO 639-2 language codes, e g, "nob, nno, eng".
`region` | (optional) a region to use as a filter for taxa search.

#### Example request

```curl
$ curl  -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'X-User-Email: <EMAIL>' -H 'X-User-Token: <TOKEN>' \
  -X PUT "http://api.biocaching.com:82/settings" \
  -d '{"settings" : { "region" : "nor"}}' \
```

#### Example response

```json
{
  "collection_id": null,
  "created_at": "2016-02-26T17:23:16.000Z",
  "id": 2,
  "languages": "nob,eng",
  "region": "",
  "updated_at": "2016-02-26T17:23:44.000Z",
  "user_id": 3
}
```
