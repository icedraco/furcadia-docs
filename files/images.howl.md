---
classification: public
---

# images.howl - Furcadia Image Cache
## Overview
This [HOWL](../formats/HOWL.md) file is a local database of downloaded Furcadia
images (e.g., description tags), used as a cache.

## Table: file_cache
| Column        | Description                      |
| ------------- | -------------------------------- |
| file_id       | Furcadia desctag ID              |
| file_name     | URL of the image                 |
| file_mime     | Always "image/png"               |
| file_type     | Always **49230**                 |
| file_size     | Size of the data in bytes        |
| date_created  | Creation date                    |
| date_accessed | Last access date (for cache LRU) |
| data          | Payload; binary data             |

### Example
| file_id   | file_name                                              | file_mime | file_type | file_size | date_created        | date_accessed       | data   |
| :-------- | :----------------------------------------------------- | :-------- | --------: | --------: | :------------------ | :------------------ | :----- |
| 400001411 | http://apollo.furcadia.com/cache/400001411.png         | image/png |     49230 |      2099 | 2024-08-25 04:47:45 | 2024-09-15 15:53:46 | PNG... |
| 7         | http://apollo.furcadia.com/cache/7-dt-share-fb.png     | image/png |     49230 |      1113 | 2024-08-25 04:47:45 | 2024-09-10 18:45:11 | PNG... |
| 400000080 | http://apollo.furcadia.com/cache/400000080.png         | image/png |     49230 |      1187 | 2024-08-25 04:47:45 | 2024-08-28 15:52:29 | PNG... |
| 10        | http://apollo.furcadia.com/cache/10-dt-share-t-sml.png | image/png |     49230 |      1030 | 2024-08-25 04:47:46 | 2024-08-25 04:47:46 | PNG... |
| 590000011 | http://apollo.furcadia.com/cache/590000011.png         | image/png |     49230 |       467 | 2024-08-25 07:11:48 | 2024-08-25 07:11:48 | PNG... |
| 610000225 | http://apollo.furcadia.com/cache/610000225.png         | image/png |     49230 |       322 | 2024-08-25 07:31:41 | 2024-08-25 07:31:41 | PNG... |

## Table: horus_manifest
| name    | value                                  |
| ------- | -------------------------------------- |
| magic   | Horus Official Whatchamacallit Library |
| format  | 10401                                  |
| version | 100                                    |
| flags   | 0                                      |
| user1   | 0                                      |
| user2   | 0                                      |

-------------------------------------------------------------------------------

## Reference
* [HOWL](../formats/HOWL.md) - Horus Official Whatchamacallit Library format
