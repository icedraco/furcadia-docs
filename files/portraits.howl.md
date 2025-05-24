---
classification: public
---

# portraits.howl - Furcadia Portrait Cache
## Overview
This [HOWL](../formats/HOWL.md) file is a local database of downloaded Furcadia
portrait images, used as a cache.

## Table: file_cache
| Column        | Description                                               |
| ------------- | --------------------------------------------------------- |
| file_id       | Furcadia portrait ID                                      |
| file_name     | Always empty                                              |
| file_mime     | Always "furcadia/portrait"                                |
| file_type     | Always **20952**                                          |
| file_size     | Size of the data in bytes                                 |
| date_created  | Creation date                                             |
| date_accessed | Last access date (for cache LRU)                          |
| data          | Payload; binary data in [FCPT](../formats/FCPT.md) format |

### Example
| file_id | file_name | file_mime         | file_type | file_size | date_created        | date_accessed       | data    |
| :------ | :-------- | :---------------- | --------: | --------: | :------------------ | :------------------ | :------ |
| 216787  |           | furcadia/portrait |     20952 |     27099 | 2024-08-25 04:47:27 | 2024-08-25 04:47:27 | fcpt... |
| 249074  |           | furcadia/portrait |     20952 |     27099 | 2024-08-25 10:41:31 | 2024-08-25 10:41:31 | fcpt... |
| 253844  |           | furcadia/portrait |     20952 |     27099 | 2024-08-25 17:29:11 | 2024-08-25 17:29:11 | fcpt... |
| 253567  |           | furcadia/portrait |     20952 |     27099 | 2024-08-26 06:53:41 | 2024-08-26 06:53:41 | fcpt... |
| 140784  |           | furcadia/portrait |     20952 |      9049 | 2024-08-26 14:08:29 | 2024-08-26 14:08:29 | fcpt... |

## Table: horus_manifest
| name    | value                                  |
| ------- | -------------------------------------- |
| magic   | Horus Official Whatchamacallit Library |
| format  | 10401                                  |
| version | 100                                    |
| flags   | 0                                      |
| user1   | 0                                      |
| user2   | 0                                      |

## Reference
* [HOWL](../formats/HOWL.md) - Horus Official Whatchamacallit Library format
