storm-sample
============

Sample code for building storm topologies in Hortonworks HDP.

This is not a complete or working solution but provides all the necessary sample bits to get a storm project started.

Getting started:

- Look under src/main/java/com/hortonworks/streaming/impl
- In the topologies directory we can see the Storm topology (base class and implemented class)
- Under bolts you can see bolts for HDFS (with rotation), hive and solr
- The StormKafka scheme is under the kafka directory
  - All items in this topology are optional, you can disable everything but the Kafka spout to start,
    and add bolts as needed.

- Look under src/main/resources
- Modify everything in config.properties and hbase-site.xml to match your environment

Compile:

mvn compile

Build:

mvn package

Deploy Example script:

#!/bin/sh
scp target/<topology>.jar <storm client server>:
scp src/main/resources/config.properties <storm client server>:
ssh <storm client server> <<'ENDSSH'
storm jar <topology>.jar <topology main class> config.properties
ENDSSH

<topology main class> would be something like com.hortonworks.streaming.impl.topologies.BellStormKafkaTopology

Any questions about the code can be directed to pwendorf AT hortonworks DOT com