# MongoDB Sharding

## Config servers

`mongod --configsvr --replSet confrs --port 27017 --dbpath /data/db`

### Replica set config 

    rs.initiate(
    {
       _id: "confrs",
       configsvr: true,
       members: [
        { _id : 0, host : "<host>:<port>" },
        ]
    })

## Shard server

`mongod --shardsvr --replSet shard1rs --port 27017 --dbpath /data/db`

### Replic set config
   
    rs.initiate(
      {
        _id: "shard1rs",
        members: [
          { _id : 0, host : "139.59.31.201:30001" },
    
        ]
      }
    )
## Mongos Router

` mongos --configdb confrs/<host>:<port> --bind_ip 0.0.0.0 --port 27017`

## Sharding commands

 `sh.enableSharding('dbname')`
 
 `sh.shardCollection('db.collname',{'sharding_key':'type'})`

## Mongo Document import command 

`mongoimport --host <host string>:<port> --db test --collection gpsdata --file <path to json file> --jsonArray`