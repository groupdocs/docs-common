---
id: installation
url: search/java/installation
title: Installation
weight: 5
description: ""
keywords: 
productName: GroupDocs.Search for Java
hideChildren: False
---
## Development Environment

### Operating Systems

**GroupDocs.Search for Java** can be executed on any Operating System with Java JDK installed.

*   Windows Desktops and Servers
*   Linux
*   Mac OS

### Supported Runtime

**GroupDocs.**Search **for Java** supports Java run-time version 6 (1.6) and above.

### Development Environments

*   NetBeans
*   IntelliJ IDEA
*   Eclipse

## Installation from GroupDocs Artifactory using Maven

GroupDocs hosts all Java APIs on [GroupDocs Artifactory](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo). You can easily use GroupDocs.Search for Java API directly in your Maven projects with simple configurations.

### Specify GroupDocs Repository Configuration

First, you need to specify GroupDocs repository configuration/location in your Maven `pom.xml` as follows:

**XML**

```csharp
<repositories>
	<repository>
		<id>GroupDocsJavaAPI</id>
		<name>GroupDocs Java API</name>
		<url>http://repository.groupdocs.com/repo/</url>
	</repository>
</repositories>
```

### Define GroupDocs.Search for Java API Dependency

Then define GroupDocs.Search for Java API dependency in your `pom.xml` as follows:

**XML**

```csharp
<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-search</artifactId>
        <version>19.10</version> 
    </dependency>
</dependencies>
```

After performing above-mentioned steps, GroupDocs.Search for Java dependency will finally be added to your Maven project.
