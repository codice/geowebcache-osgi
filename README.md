<!--
/*
 * Copyright (c) Codice Foundation
 *
 * This is free software: you can redistribute it and/or modify it under the terms of the GNU Lesser General Public License as published by the Free Software Foundation, either
 * version 3 of the License, or any later version. 
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * See the GNU Lesser General Public License for more details. A copy of the GNU Lesser General Public License is distributed along with this program and can be found at
 * <http://www.gnu.org/licenses/lgpl.html>.
 */
-->

# GeoWebCache 
## Introduction
This project embeds the GeoWebCache (http://geowebcache.org) server into an OSGi bundle that can be run on an OSGi 4.2+ container.

When deployed in an OSGi container, all the normal GeoWebCache functions are available including:
- WMS/WMTS endpoints (/geowebcache/service)
- RESTful webservices for GeoWebCache configuration (/geowebcache/rest)
- Caching of tiles
- Seeding of tiles 

## Building
### What you need ###
* [Install J2SE 8 SDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
* Make sure that your JAVA\_HOME environment variable is set to the newly installed JDK location, and that your PATH includes %JAVA\_HOME%\bin (Windows) or $JAVA\_HOME$/bin (\*NIX).
* [Install Maven 3.0.3 \(or later\)](http://maven.apache.org/download.html). Make sure that your PATH includes the MVN\_HOME/bin directory.
* Set the MAVEN_OPTS variable with the appropriate memory settings

### How to build ###
```
git clone git://github.com/codice/geowebcache-osgi.git
```
Change to the top level directory of geowebcache-osgi source distribution.

```
mvn install
```

## Notes
### Spring Security Config
WEB-INF/acegi-config.xml was modified to
- allow anonymous access to GWC REST services
- allow anonymous access to POST/PUT/DELETE operations on GWC services
This assumes other security components are present in the OSGi container to control access to GWC paths if needed.

### Layer configuration
WEB-INF/geowebcache-core-context.xml was modified to set the XML configuration directory to the karaf etc directory.  
This can easily modified for other OSGi containers.
