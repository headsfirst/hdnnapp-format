*This document describes the format of HDNN Apps, single-file applications that can run on an HDNN Simulator.*

HDNN Apps are [SQLite](https://www.sqlite.org/) databases that adhere to the following content specification:

```CREATE TABLE GenericEntity (type STRING, id STRING, name STRING, status STRING, properties STRING)
```

, where the 'type' field can take these values: 
* 'Node'
* 'Process'
* 'Bridge'
* 'Connection'
* 'NodeModel'
* 'ProcessModel'
* 'BridgeModel'
* 'ConnectionModel'

and the 'status' field can take these values: 
* 'a' (active)
* 'i' (inactive)


```CREATE TABLE GenericRelation (entity1_id STRING, entity2_id STRING, dimension STRING, quantity FLOAT)
```

,where the 'dimension' field can take these values:
* 'm' (model)
* 'p' (parent)
* 'i' (input)
* 'o' (output)
