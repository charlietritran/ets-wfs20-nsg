## Conformance Test Suite: NSG WFS v2 Profile

### Scope

This test suite verifies that a WFS implementation conforms to the NSG Web Feature Service 
2.0 Implementation Profile, v1.0.0 ([NGA.STND.0062_2.0_WFS](https://nsgreg.nga.mil/doc/view?i=4283), 
2017-01-11). The aim is to cover the MANDATORY and RECOMMENDED capabilities stipulated in 
all relevant specifications.

Note that this profile extends and restricts the specifications upon which it is based. The 
main dependencies are:

* DGIWG Web Feature Service 2.0 Profile (DGIWG-122)
* OGC Web Feature Service standard, Version 2.0.2 [OGC 09-025r2]
* OGC Filter Encoding standard, Version 2.0.2 [OGC 09-026r2].

Visit the [project documentation website](http://opengeospatial.github.io/ets-wfs20-nsg/) 
for more information, including the API documentation.

### How to run the tests
The test suite is built using [Apache Maven v3](https://maven.apache.org/). The options 
for running the suite are summarized below.

#### 1. Integrated development environment (IDE)

Use a Java IDE such as Eclipse, NetBeans, or IntelliJ. Clone the repository and build the project.

Set the main class to run: `org.opengis.cite.wfs20-nsg.TestNGController`

Arguments: The first argument must refer to an XML properties file containing the 
required test run arguments. If not specified, the default location at `$
{user.home}/test-run-props.xml` will be used.
   
You can modify the sample file in `src/main/config/test-run-props.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE properties SYSTEM "http://java.sun.com/dtd/properties.dtd">
<properties version="1.0">
  <comment>NSG WFS 2.0 reference implementation - Test run arguments</comment>
  <entry key="wfs">http://localhost:8080/wfs?SERVICE=wfs&VERSION=2.0.0&REQUEST=GetCapabilities</entry>
</properties>
```

The TestNG results file (`testng-results.xml`) will be written to a subdirectory
in `${user.home}/testng/` having a UUID value as its name.

#### 2. Command shell (console)

One of the build artifacts is an "all-in-one" JAR file that includes the test 
suite and all of its dependencies; this makes it very easy to execute the test 
suite in a command shell:

`java -jar ets-wfs20-nsg-0.1-SNAPSHOT-aio.jar [-o|--outputDir $TMPDIR] [test-run-props.xml]`

#### 3. OGC test harness

Use [TEAM Engine](https://github.com/opengeospatial/teamengine), the official OGC test harness.
The latest test suite release are usually available at the [beta testing facility](http://cite.opengeospatial.org/te2/). 
You can also [build and deploy](https://github.com/opengeospatial/teamengine) the test 
harness yourself and use a local installation.

### How to contribute

If you would like to get involved, you can:

* [Report an issue](https://github.com/opengeospatial/ets-cat30/issues) such as a defect or 
an enhancement request
* Help to resolve an [open issue](https://github.com/opengeospatial/ets-cat30/issues?q=is%3Aopen)
* Fix a bug: Fork the repository, apply the fix, and create a pull request
* Add new tests: Fork the repository, implement and verify the tests on a new topic branch, 
and create a pull request (don't forget to periodically rebase long-lived branches so 
there are no extraneous conflicts)

### How to build the test suite

Several dependencies are not available via Central Maven Repository. Thus, these have to be built locally.

All examples of this section refer to version 0.2 of this test suite.

Clone, checkout tag (in this example version 5.0) and build **TEAM Engine dependency**.
* ```git clone https://github.com/opengeospatial/teamengine.git```
* ```cd teamengine```
* ```git checkout 5.0```
* ```mvn clean install```

Clone, checkout tag (in this example version 1.26) and build **WFS 2.0 dependency**.
* ```git clone https://github.com/opengeospatial/ets-wfs20.git```
* ```cd ets-wfs20```
* ```git checkout 1.26```
* ```mvn clean install```

Clone, checkout tag (in this example version 0.4) and build **DGIWG Core dependency**.
* ```git clone https://github.com/opengeospatial/ets-dgiwg-core.git```
* ```cd ets-dgiwg-core```
* ```git checkout 0.4```
* ```mvn clean install```

Clone, checkout tag (in this example version 0.3) and build WFS 2.0 **DGIWG Profile dependency**.
* ```git clone https://github.com/opengeospatial/ets-wfs20-dgiwg.git```
* ```cd ets-wfs20-dgiwg```
* ```git checkout 0.3```
* ```mvn clean install```

Finally, all dependencies are available.

Now, clone, checkout tag (in this example version 0.2) and build **this repository**.
* ```git clone https://github.com/opengeospatial/ets-wfs20-nsg.git```
* ```cd ets-wfs20-nsg```
* ```git checkout 0.2```
* ```mvn clean install```
