## Collections

Collections are like views on the taxonomy that can be created for different purposes and used to filter the content returned from the taxa search service.

### List collections

Returns a array of existing collections.

```endpoint
GET http://api.biocaching.com/collections
```

URL Parameters | Description
---|---
`collection_id` | (optional) get collections that have the specified collection as a parent.

#### Request headers

```http
Content-Type: application/json
Accept: application/json
X-User-Email: <EMAIL>
X-User-Token: <TOKEN>
```

#### Example request

```curl
$ curl  -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'X-User-Token: <TOKEN>' \
  -X GET "http://api.biocaching.com:82/collection" \
```
