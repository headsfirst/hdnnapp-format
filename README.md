*This document describes the format of HDNN Apps, single-file applications that can run on the HDNN Simulator.*

HDNN Apps are [SQLite](https://www.sqlite.org/) databases that adhere to the following content specification:

## Entities ##
```CREATE TABLE GenericEntity (type STRING, id STRING, name STRING, status STRING, properties STRING)```

, where the 'type' field can take these values: 
* 'Sim'
* 'Node'
* 'Switch'
* 'Bridge'
* 'Process'
* 'Connection'
* 'SimModel'
* 'NodeModel'
* 'SwitchModel'
* 'BridgeModel'
* 'ProcessModel'
* 'ConnectionModel'

, the 'status' field can take these values: 
* 'a' (active)
* 'i' (inactive)

and the 'properties' field contains a JSON string defining name-value pairs.


## Relations ##
```CREATE TABLE GenericRelation (entity1_id STRING, entity2_id STRING, dimension STRING, quantity FLOAT)```

,where the 'dimension' field can take these values:
* 'm' (model)
* 'p' (parent)
* 'i' (input)
* 'o' (output)


The general rule is that entity records have a model ('m') relation to their respective model record, for instance a Process has one ProcessModel as its model. The model name serves as the class name for the entity. Hence, which model names are supported depends on the (version of the) HDNN simulator.  

Nodes can have multiple input ('i') relations to other Nodes or to Connections. Here, the 'quantity' field serves as the connection weight.  

Connections should have a single parent ('p') relation to a Node, whereas Nodes, Bridges and Processes should each have a single parent ('p') relation to a Switch.  
