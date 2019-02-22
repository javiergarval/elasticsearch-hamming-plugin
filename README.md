# elasticsearch-hamming-plugin

## Install
```shell
$ /usr/share/elasticsearch/bin/elasticsearch-plugin install https://github.com/javiergarval/elasticsearch-hamming-plugin/releases/download/v0.0.2/v0.0.2.zip
$ echo "script.inline: true$'\r'script.stored: true" >> /etc/elasticsearch/elasticsearch.yml
```

## Usage
POST `/{index_name}/_search` :
```json
{
  "query": {
    "function_score": {
      "query": {
        "match_all": {}
      },
      "functions": [
        {
          "script_score": {
            "script": {
              "inline": "hamming_distance_native",
              "lang": "native",
              "params": {
                "hash": "3dd3c609f30cd16c",
                "field": "phash"
              }
            }
          }
        }
      ]
    }
  }
}
```
