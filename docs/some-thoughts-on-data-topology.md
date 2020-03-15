# Some thoughts on data topology

## Through patches of entangled weeds in data world

If you are someone who has been working in big data area for a while, you must have been dealing with following questions day in and day 
out. 

- where is the data stored?
- where does the data come from?
- which part generates the data?
- what is the schema of the data?
- which systems consume the data?
- is the job processing the data healthy?
- what kind of processing is applied to the data?
- ...

In the place I work for, it's not always easy to get a straight answer to any of the questions. Actually, in many cases, it's like crawling 
through patches of entangled weeds one after another to get an answer. I think there are many reasons.
- so many technologies involved
  - for storing data, HDFS, Teradata, Swift, Cassandra, Couchbase, Mongo, Elasticsearch, etc.
  - for processing data, Hadoop MapReduce (obsolete but legacy is there), Spark, Flink, Storm, Teradata SQL, scripts in different languages,
   etc.
- so many components involved
  - often written in different languages
  - often run on different platforms
  - many that you and your team don't have control
- information and knowledge are scattered
  - among all kinds of documents
  - among codes in different code bases
  - among minds of different people

I have been looking for something that can not only give straight answers to most of the questions, but also provide an integrated view,
 which is more complete and offers enough clarity, about what components the system consists of, what each component does, how data flows 
 through the components, including what's in upstream team's control, in my team's scope, and in downstream team's territory.

But so far no satisfactory finding. Orchestration solutions like UC4, Spring Cloud DataFlow, AirFlow, are probably the closest ones, 
they could provide very nice view of work flow, showing processing steps and DAG, but they don't help too much w.r.t answering questions 
like where the data is stored or what is the schema, and they can't tell anything goes beyond what's orchestrated and scheduled.

So I've been thinking about how to build such a something and also doing some research, the result is some idea called data topology, which 
might worth sharing. 

## Idea of data topology

First of all, I have to make it very clear, data topology is a reflection of running system where data flows from begin to end, not running 
system itself.

Data topology is formed around 3 basic elements.

![](pics/data-actor-and-data-container.png)

- data actor, which is reflection/representation of running unit does something about data, with storing/containing data excluded.
- data container, which is reflection/representation of running unit which contains data, could be a Kafka Topic, or a Cassandra table in a 
keyspace, a Couchbase bucket, a HDFS directory or a file within a directory, a HIVE table, an OpenSwift container, an Elasticsearch index, 
a MySQL table, etc.
- arrowed line, an arrow represents data flow direction, while the line reflects the coupling/connection between two components, either 
actor or container.

Here are the explanation on how everything works.
- data actor can connect with data container or data actor
- data container cannot connect with data container
- one data actor can connect with multiple data containers and/or multiple data actors
- arrow indicates data flow and direction
- when data flows through a data actor, some processing happens, it could be as simple as copying
- an arrow leading out of a data container means data flows out of the data container
- an arrow leading into a data container means data flows into the data container
- an arrow leading into a data actor means the data actor takes in data then processes it
- an arrow leading out of data actor means the data actor finishes processing then lets processed data flows toward downstream component
- data actor can have many information attached, such as underlying system information, setting of connection to data container or another 
data actor, how to probe itself and connectivity with other components, what kind of processing it applies to data flowed-in, link to 
source code, etc.
- data container can also have many information attached, such as cluster information, how to probe cluster and the container, DDL scripts, 
data schemas, how to inspect data contained, etc.

Below is one sample data topology as a reflection of real data processing pipeline, data service and end applications consume data, without 
revealing details. User could not only get a full picture, but could also interact with each component on the topology to get information 
needed for operating, inspection, triaging and monitoring.

![](pics/sample-data-topology.png)

## Summary

The idea of data topology described here is one step closer to what I have been looking for. 
- it could provide a more complete picture of a running data system
- it could capture/bring key information together, hence provide easy access to those information for everyday work.

Next step is probably to work on a PoC.
