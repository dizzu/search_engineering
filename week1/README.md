```shell
export HOST=gen-docker43786
export BBUY_DATA=/home/ovidiu.mihalcea/search_engineering/datasets/product_data/products
export WEEK1_PATH=/home/ovidiu.mihalcea/search_engineering/search_engineering/week1
export QUERY_FILE=/home/ovidiu.mihalcea/search_engineering/datasets/bbuy/train.csv
```
# Level 1

```shell
$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 5.6233855840333336 minutes.  Total accumulated time spent in `bulk` indexing: 16.57116598336614 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 5.262134619599995 minutes.  Total accumulated time spent in `bulk` indexing: 14.182981057533077 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST --refresh_interval -1 # after setting refresh_interval setting
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 5.116996883200015 minutes.  Total accumulated time spent in `bulk` indexing: 13.377174200266746 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST --refresh_interval 1s
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of 1s to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 5.248263356733332 minutes.  Total accumulated time spent in `bulk` indexing: 14.04822715128236 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST --refresh_interval 60s
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of 60s to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 5.248123199116647 minutes.  Total accumulated time spent in `bulk` indexing: 14.14161639756679 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -b 400
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 400 per batch.
INFO:Done. 1275077 were indexed in 4.998363023700009 minutes.  Total accumulated time spent in `bulk` indexing: 12.115509924100175 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -b 800
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 800 per batch.
INFO:Done. 1275077 were indexed in 4.9819929996 minutes.  Total accumulated time spent in `bulk` indexing: 12.282010188749943 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -b 1600
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 1600 per batch.
INFO:Done. 1275077 were indexed in 4.94867772518331 minutes.  Total accumulated time spent in `bulk` indexing: 12.244663600566886 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -b 3200
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 3200 per batch.
INFO:Done. 1275077 were indexed in 4.928616096866668 minutes.  Total accumulated time spent in `bulk` indexing: 11.321873293533281 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -b 5000
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 8 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 5000 per batch.
INFO:Done. 1275077 were indexed in 5.12959369821668 minutes.  Total accumulated time spent in `bulk` indexing: 12.124527352383181 minutes

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -w 16
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 16 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 3.0706660975833375 minutes.  Total accumulated time spent in `bulk` indexing: 17.182828398633806 minutes
### best so far - 16 core machine with 16 workers, almost 100% CPU usage

-----

$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products_no_map.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -w 32
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 32 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 200 per batch.
INFO:Done. 1275077 were indexed in 2.896040724966679 minutes.  Total accumulated time spent in `bulk` indexing: 31.110110389199175 minutes
### it just gets worse from here as the CPU usage on the machine increases over 100%
```

# Level 2
```shell
$ curl -k -X DELETE -u admin:admin https://$HOST:9200/bbuy_products
{"acknowledged":true}

$ curl -k -X PUT -u admin:admin https://$HOST:9200/bbuy_products -H 'Content-Type: application/json' -d @$WEEK1_PATH/bbuy_products.json
{"acknowledged":true,"shards_acknowledged":true,"index":"bbuy_products"}

$ python index.py -s $BBUY_DATA -o $HOST -w 16 -b 400
INFO:Indexing /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/product_data/products to bbuy_products with 16 workers, refresh_interval of -1 to host gen-docker43786-all-dev.mwp-tsl.e5.c.emag.network with a maximum number of docs sent per file per worker of 200000 and 400 per batch.
INFO:Done. 1275077 were indexed in 2.975998716566634 minutes.  Total accumulated time spent in `bulk` indexing: 16.188137316698523 minutes
### optimal so far - 16 core machine with 16 workers with 400 per batch, almost 100% CPU usage

------------------------------------------------------------

# default settings
$ python query.py -o $HOST -q $QUERY_FILE -m 10000
INFO:Loading query file from /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/train.csv
INFO:Running queries, checking in every 1000 queries:
INFO:Query: Bad teacher has 10 hits.
INFO:Query: martin has 10 hits.
INFO:Query: netgear n has 10 hits.
INFO:Query: iPad case has 10 hits.
INFO:Query: digital tv converter has 10 hits.
INFO:Query: Bluetooth has 10 hits.
INFO:Query: Xbox 360 battery charger has 10 hits.
INFO:Query: Bose sound dock has 10 hits.
INFO:Query: HP touchpad has 10 hits.
INFO:Query: rechargeable batteries has 10 hits.
INFO:Finished running 10000 queries in 3.9004943366166116 minutes
-----
# no fuzziness
$ python query.py -o $HOST -q $QUERY_FILE -m 10000
INFO:Loading query file from /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/train.csv
INFO:Running queries, checking in every 1000 queries:
INFO:Query: Bad teacher has 10 hits.
INFO:Query: martin has 10 hits.
INFO:Query: netgear n has 10 hits.
INFO:Query: iPad case has 10 hits.
INFO:Query: digital tv converter has 10 hits.
INFO:Query: Bluetooth has 10 hits.
INFO:Query: Xbox 360 battery charger has 10 hits.
INFO:Query: Bose sound dock has 10 hits.
INFO:Query: HP touchpad has 10 hits.
INFO:Query: rechargeable batteries has 10 hits.
INFO:Finished running 10000 queries in 3.3542500556666104 minutes
-----
# no fuzziness, no function scores
$ python query.py -o $HOST -q $QUERY_FILE -m 10000
INFO:Loading query file from /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/train.csv
INFO:Running queries, checking in every 1000 queries:
INFO:Query: Bad teacher has 10 hits.
INFO:Query: martin has 10 hits.
INFO:Query: netgear n has 10 hits.
INFO:Query: iPad case has 10 hits.
INFO:Query: digital tv converter has 10 hits.
INFO:Query: Bluetooth has 10 hits.
INFO:Query: Xbox 360 battery charger has 10 hits.
INFO:Query: Bose sound dock has 10 hits.
INFO:Query: HP touchpad has 10 hits.
INFO:Query: rechargeable batteries has 10 hits.
INFO:Finished running 10000 queries in 2.7434468240166705 minutes
-----
# no fuzziness, no function scores, no other matching function except the multi_match
$ python query.py -o $HOST -q $QUERY_FILE -m 10000
INFO:Loading query file from /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/train.csv
INFO:Running queries, checking in every 1000 queries:
INFO:Query: Bad teacher has 5 hits.
INFO:Query: martin has 10 hits.
INFO:Query: netgear n has 10 hits.
INFO:Query: iPad case has 10 hits.
INFO:Query: digital tv converter has 10 hits.
INFO:Query: Bluetooth has 10 hits.
INFO:Query: Bose sound dock has 10 hits.
INFO:Query: HP touchpad has 10 hits.
INFO:Query: rechargeable batteries has 10 hits.
INFO:Finished running 10000 queries in 1.9577701335666764 minutes
-----
# no fuzziness, no function scores, no other matching function except the multi_match, the multi_match only searches the name and shortDescription field.
$ python query.py -o $HOST -q $QUERY_FILE -m 10000
INFO:Loading query file from /home/ovidiu.mihalcea/search_engineering/datasets/bbuy/train.csv
INFO:Running queries, checking in every 1000 queries:
INFO:Query: Bad teacher has 5 hits.
INFO:Query: martin has 10 hits.
INFO:Query: netgear n has 10 hits.
INFO:Query: iPad case has 10 hits.
INFO:Query: digital tv converter has 8 hits.
INFO:Query: Bluetooth has 10 hits.
INFO:Query: HP touchpad has 10 hits.
INFO:Query: rechargeable batteries has 10 hits.
INFO:Finished running 10000 queries in 1.2622880030333665 minutes
```