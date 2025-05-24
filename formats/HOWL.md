# HOWL - Horus Official Whatchamacallit Library
## Overview
HOWL files are SQLite3 database files that are currently used to cache Furcadia
images and portraits.

## Location
* Localdir: `<localdir_path>/portraits/`

## Structure
### Table: file_cache
Contains the cached data (blob) and cache-specific information about it.

```sql
CREATE TABLE file_cache (
	[file_id]       integer(10) UNIQUE NOT NULL DEFAULT 0,
	[file_name]     varchar(128) NOT NULL,
	[file_mime]     varchar(128) NOT NULL,
	[file_type]     integer(10)  NOT NULL,
	[file_size]     integer(10)  NOT NULL,
	[date_created]  datetime     NOT NULL,
	[date_accessed] datetime     NOT NULL,
	[data]          blob         NOT NULL,
	Primary Key (file_id)
);

CREATE INDEX [fc_date_accessed] 
	On [file_cache] ( [date_accessed] );
```

##### Known Values: file_mime
* `furcadia/portrait` (see [portraits.howl](../files/portraits.howl.md))
* `image/png` (see [images.howl](../files/images.howl.md))

##### Known Values: file_type
* 20952 - used for Furcadia portraits (see [portraits.howl](../files/portraits.howl.md))
* 49230 - used for PNG images (see [images.howl](../files/images.howl.md))

-------------------------------------------------------------------------------

### Table: horus_manifest
Contains metadata for the file in a form of key-value pairs, such as format
descriptor, version of the file, etc.

```sql
CREATE TABLE horus_manifest (
	[name]  varchar(32) UNIQUE NOT NULL,
	[value] varchar(64)        NOT NULL
);
```

##### Example Content
The following content was found both in a `portraits.howl` and `images.howl`
file.

| name    | value                                  |
| ------- | -------------------------------------- |
| magic   | Horus Official Whatchamacallit Library |
| format  | 10401                                  |
| version | 100                                    |
| flags   | 0                                      |
| user1   | 0                                      |
| user2   | 0                                      |
* TODO: Describe the nature of `flags`, `user1`, `user2` - currently unknown

-------------------------------------------------------------------------------

## Reference
* [images.howl](../files/images.howl.md) - image cache
* [portraits.howl](../files/portraits.howl.md) - portrait cache
