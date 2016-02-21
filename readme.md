mquery
======

The goal of the `mquery` project is to access a [mongoDB](https://www.mongodb.org/) from command line. 

### Dependencies

```bash
pip install pymongo
pip install configparser
```

### Configuration

A first run creates *.mquery* file in current users home directory, if not present. There must be at least on *DEFAULTS* section and one *SYSTEM* settings. For details see the documentation for [configparser](https://docs.python.org/3.5/library/configparser)

```
[DEFAULTS]
defaultsystem = LOCAL 

# System list
[LOCAL]
url = localhost

[PROD]
url = prod.foo.com 
user = username
password = password

[QA]
url = qa.foo.com 
user = username
password = password

#...
```

### Parameter

```
usage: mquery [-h] [-s {LOCAL,PROD,QA}]
              [-d DATABASE] [-c COLLECTION] [-q QUERY] [-p PROJECTION] [-C]
              [-F] [-L] [-D DISTINCT] [-i INCLUDE [INCLUDE ...]]
              [-e EXCLUDE [EXCLUDE ...]] [-v VERBOSE [VERBOSE ...]] [-l LIMIT]
              [-1 SORTASCENDING [SORTASCENDING ...]]
              [-2 SORTDESCENDING [SORTDESCENDING ...]]

optional arguments:
  -h, --help            show this help message and exit
  -s {LOCAL,PROD,QA}, --system {LOCAL,PROD,QA}
                        choose system configured in ~/.mquery
  -d DATABASE, --database DATABASE
                        choose database
  -c COLLECTION, --collection COLLECTION
                        choose collection to query
  -q QUERY, --query QUERY
                        get query (json)
  -p PROJECTION, --projection PROJECTION
                        raw json projection
  -C, --count           count documents for given cursor
  -F, --followCount     show insert velocity. depends on -C/--count. counts
                        every second
  -L, --listCollections
                        show collections for given database
  -D DISTINCT, --distinct DISTINCT
                        distinct field for cursor
  -i INCLUDE [INCLUDE ...], --include INCLUDE [INCLUDE ...]
                        include fields
  -e EXCLUDE [EXCLUDE ...], --exclude EXCLUDE [EXCLUDE ...]
                        exclude field
  -v VERBOSE [VERBOSE ...], --verbose VERBOSE [VERBOSE ...]
                        verbose output. seperate values by dash. compact view.
                        projects fields.
  -l LIMIT, --limit LIMIT
                        limits cursor
  -1 SORTASCENDING [SORTASCENDING ...], --sortAscending SORTASCENDING [SORTASCENDING ...]
                        sort field
  -2 SORTDESCENDING [SORTDESCENDING ...], --sortDescending SORTDESCENDING [SORTDESCENDING ...]
                        sort field
```

### Contact

Jan Frederik Hake, <jan_hake@gmx.de>. [@enter\_haken](https://twitter.com/enter_haken) on Twitter.
