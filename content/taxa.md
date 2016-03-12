## Taxa

The Taxa services give access to the species database.

### Retrieve a subset of taxa

Called with no extra parameters, this service returns the taxa with rank `kingdom`.

```endpoint
GET http://api.biocaching.com/taxa
```

URL Parameters | Description
---|---
`from` | (optional) return a subset of the taxa, start at ´from´, default = 0.
`size` | (optional) return ´size´ number of taxa, default = 10.
`parent_id` | (optional) return taxa that are immediate children of another taxa. If omitted, return taxa on the highest level (the kingdoms: `animalia`, `plantae` and `fungi`).
`fields` | (optional) if omitted, only a subsets of the available fields are included in the response. Pass value "all" to have all available fields returned.
`region` | (optional) only return taxa that are found in a specific region. For now, only region ´nor´ is available.

#### Request headers

```http
Content-Type: application/json
Accept: application/json
X-User-Email: <EMAIL>
X-User-Token: <TOKEN>
```

### Retrieve a single taxon

```endpoint
GET http://api.biocaching.com/taxa/{ID}
```

URL Parameters | Description
---|---
`fields` | (optional) if omitted, only a subsets of the available fields are included in the response. Pass value "all" to have all available fields returned.

#### Request headers

```http
Content-Type: application/json
Accept: application/json
X-User-Email: <EMAIL>
X-User-Token: <TOKEN>
```

#### Example Request

```curl
$ curl  -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'X-User-Email: <EMAIL>' -H 'X-User-Token: <TOKEN>' \
  -X GET "http://api.biocaching.com:82/taxa/345" \
```

#### Example Response

```json
{
  "total": 1,
  "max_score": 1,
  "number_of_hits": 1,
  "hits": [
    {
      "_id": "345",
      "_index": "taxa",
      "_score": 1,
      "_source": {
        "id": 345,
        "parent_id": 342,
        "ranks": [
          {
            "language_iso": "eng",
            "rank": "not assigned"
          }
        ],
        "scientific_name": "hippopotamus amphibius kiboko",
        "source": {
          "source_database": {
            "authors_and_editors": "Orrell T. (custodian)",
            "id": 1,
            "name": "ITIS Global: The Integrated Taxonomic Information System",
            "uri": "http://www.itis.gov;↵http://www.cbif.gc.ca/acp/eng/itis/search (Canada)",
            "uri_scheme": "http"
          },
          "taxonomy": "Species 2000 & ITIS Catalogue of Life: 2013 Annual Checklist"
        }
      }
      "type": "taxon"
    }
  ]
}
```

### Search for taxa

Search for taxa.

```endpoint
GET http://api.biocaching.com/taxa/search?term={STRING}
```

URL Parameters | Description
---|---
`term` | search for search_term in scientific and common names of taxa with rank genus, species and infraspecific.
`from` | (optional) return a subset of the taxa, start at ´from´, default = 0.
`size` | (optional) return ´size´ number of taxa, default = 10.
`below_rank`, `below_rank_value` | (optional) return only taxa below a certain rank in the taxonomy.
`fields` | (optional) if omitted, only a subsets of the available fields are included in the response. Pass value "all" to have all available fields returned.
`region` | (optional) only return taxa that are found in a specific region. For now, only region ´nor´ is available.
`languages` | (optional) only return taxa that have common names in one of the specified languages (ISO 639-2), default is ´eng´.
`collection_id` | (optional) only return taxa within a collection.

#### Request headers

```http
Content-Type: application/json
Accept: application/json
X-User-Email: <EMAIL>
X-User-Token: <TOKEN>
```
