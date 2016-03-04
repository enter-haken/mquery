mquery
======

The goal of the `mquery` project is to access a [mongoDB](https://www.mongodb.org/) from command line. 

### Dependencies

```bash
pip install pymongo
pip install configparser
```

### Configuration

A first run creates *.mquery.yaml* file in current users home directory, if not present. There must be at least on *defaults* section and one *systems* settings. For details see the documentation for [yaml](http://pyyaml.org/)

```
defaults:
    defaultsystem : PROD

systems:
    LOCAL:
        description: "local database"
        url : localhost
```

#### systems

You need at least an url for the database server. 
You can additionally apply a *user* and a *password*. 
The credentials will be authenticated against the *admin* database.


```
PROD:
    description: "prod foo database"
    url : prod.foo.com 
    user : username 
    password : password
DEV:
    description: "dev foo database"
    url : dev.foo.com 
    user : username 
    password : password
```

The description is optional, and will appear in the help.

#### queries

Frequent queries can be stored in the *queries* section.

```
queries:
    getImportantData:
        description: "it is important"
        collection: ImportantDataCollection
        query:
            Foo: Bar
        fields: 
            _id: 1
            Foo: 1
        verbose: false
```

This will be translated to:

```
db.ImportantDataCollection.find({
    "Foo": "Bar"
}, {
    "_id": 1,
    "Foo": 1
});
```

These queries can be combined / merged with other search parameter.
The description is optional, and will appear in the help.

### Parameter

```
usage: mquery [-h] [-s {LOCAL,BWIDEV,QA,ARCHIV,PROD,BWIQA,DEV,HAKE}]
              [-d DATABASE] [-c COLLECTION] [-q QUERY] [-D DISTINCT]
              [-p PROJECTION] [-f] [-C] [-F] [-o] [-L]
              [-i INCLUDE [INCLUDE ...]] [-e EXCLUDE [EXCLUDE ...]]
              [-v VERBOSE [VERBOSE ...]] [-l LIMIT]
              [-1 SORTASCENDING [SORTASCENDING ...]]
              [-2 SORTDESCENDING [SORTDESCENDING ...]]

query the mongo

optional arguments:
  -h, --help            show this help message and exit
  -s {LOCAL}, --system {LOCAL}
                        LOCAL - local database
 -d DATABASE, --database DATABASE
                        choose database
  -c COLLECTION, --collection COLLECTION
                        choose collection to query
  -q QUERY, --query QUERY
                        get query (json)
  -D DISTINCT, --distinct DISTINCT
                        distinct field for cursor
  -p PROJECTION, --projection PROJECTION
                        raw json projection
  -f, --fields          get fields from first document
  -C, --count           count documents for given cursor
  -F, --followCount     show insert velocity. depends on -C/--count. counts every second
  -o, --opLog           follow the op log entries one per second
  -L, --listCollections
                        show collections for given database
  -i INCLUDE [INCLUDE ...], --include INCLUDE [INCLUDE ...]
                        include fields
  -e EXCLUDE [EXCLUDE ...], --exclude EXCLUDE [EXCLUDE ...]
                        exclude field
  -v VERBOSE [VERBOSE ...], --verbose VERBOSE [VERBOSE ...]
                        verbose output. separate values by dash. compact view. projects fields.  
  -l LIMIT, --limit LIMIT
                        limits cursor
  -1 SORTASCENDING [SORTASCENDING ...], --sortAscending SORTASCENDING [SORTASCENDING ...]
                        sort field
  -2 SORTDESCENDING [SORTDESCENDING ...], --sortDescending SORTDESCENDING [SORTDESCENDING ...]
                        sort field
```

### Contact

Jan Frederik Hake, <jan_hake@gmx.de>. [@enter\_haken](https://twitter.com/enter_haken) on Twitter.
