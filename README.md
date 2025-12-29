# meta-zone
Aggregator for the [JudahZone](https://github.com/jeffmasty/JudahZone) project

build all: 
mvn -T1C -DskipTests clean install

build zone-core:
mvn -pl :zone-core -am -DskipTests clean install