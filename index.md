  ![](pictures/draft.png)

## 1 Preface

### 1.1 Aim of the specification

This E-ARK specification is part of a family of specifications that provide a common set of requirements for packaging digital information. These specifications are based on common, international standards for transmitting, describing and preserving digital data. They have been produced to help data creators, software developers and digital archives tackle the challenge of short-, medium- and long-term data management and reuse in a sustainable, authentic, cost-efficient, manageable and interoperable way. 

The foundation for these specifications is the Reference Model for an Open Archival Information System (OAIS) which has Information Packages at its core. Familiarity with the core functional entities of OAIS is a prerequisite for understanding the specifications. A visualisation of the current specification network can be seen here:

 
  ![](pictures/The_E-ARK_specification_dependency_hierarchy.png)
 
   
  **The E-ARK specification dependency hierarchy**
 
<table>
<thead>
<tr class="header">
<th>Specification</th>
<th>Aim and Goals</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Common Specification for Information Packages</td>
<td><p>This document introduces the concept of a Common Specification for Information Packages (CSIP). Its three main purposes are to:</p>
<ul>
<li><p>Establish a common understanding of the requirements which need to be met in order to achieve interoperability of Information Packages.</p></li>
<li><p>Establish a common base for the development of more specific Information Package definitions and tools within the digital preservation community.</p></li>
<li><p>Propose the details of an XML-based implementation of the requirements using, to the largest possible extent, standards which are widely used in international digital preservation.</p></li>
</ul>
<p>Ultimately the goal of the Common Specification is to reach a level of interoperability between all Information Packages so that tools implementing the Common Specification can be adopted by institutions without the need for further modifications or adaptations.</p></td>
</tr>
<tr class="even">
<td>E-ARK SIP</td>
<td><p>The main aims of this specification are to:</p>
<ul>
<li><p>Define a general structure for a Submission Information Package format suitable for a wide variety of archival scenarios, e.g. document and image collections, databases or geographical data.</p></li>
<li><p>Enhance interoperability between Producers and Archives.</p></li>
<li><p>Recommend best practices regarding metadata, content and structure of Submission Information Packages.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>E-ARK AIP</td>
<td><p>The main aims of this specification are to:</p>
<ul>
<li><p>Define a generic structure of the AIP format suitable for a wide variety of data types, such as document and image collections, archival records, databases or geographical data.</p></li>
<li><p>Recommend a set of metadata related to the structural and the preservation aspects of the AIP as implemented by the reference implementation eArchiving ToolBox (formerly earkweb).</p></li>
<li><p>Ensure the format is suitable to store large quantities of data.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>E-ARK DIP</td>
<td><p>The main aims of this specification are to:</p>
<ul>
<li><p>Define a generic structure of the DIP format suitable for a wide variety of archival records, such as document and image collections, databases or geographical data.</p></li>
<li><p>Recommend a set of metadata related to the structural and access aspects of the DIP.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Content Information Type Specifications</td>
<td><p>The main aim and goal of a Content Information Type Specification is to:</p>
<ul>
<li><p>Define, in technical terms, how data and metadata must be formatted and placed within a CSIP Information Package in order to achieve interoperability in exchanging specific Content Information.</p></li>
</ul>
<p>The number of possible Content Information Type Specifications is unlimited.</p></td>
</tr>
</tbody>
</table>



### 1.2 Organisational support

This specification is maintained by the Digital Information LifeCycle Interoperability Standards Board (DILCIS Board). The DILCIS Board ([http://dilcis.eu/](http://dilcis.eu/)) was created to enhance and maintain the draft specifications developed in the European Archival Records and Knowledge Preservation Project (E-ARK project) which concluded in January 2017 ([http://eark-project.com/](http://eark-project.com/)<span style="text-decoration:underline;">)</span>. The Board consists of eight members, but there is no restriction on the number of participants in the work. All Board documents and specifications are stored in GitHub ([https://github.com/DILCISBoard](https://github.com/DILCISBoard)) while published versions are made available on the Board webpage. Since 2018 the DILCIS Board has been responsible for the core specifications in the Connecting Europe Facility eArchiving Building Block ([https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/eArchiving](https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/eArchiving)<span style="text-decoration:underline;">)</span>.



### 1.3 Authors

A full list of contributors to this specification, as well as the revision history can be found in Appendix 1.

**TABLE OF CONTENTS**

**[2 Context](#2-context)** 

> [2.1 Purpose](#21-purpose) 
>
> [2.2 Layered data model](#22-layered-data-model) 
>
> [2.3 The boundaries of this specification and the
> SIARD-specification](#23-the-boundaries-of-this-specification-and-the-siard-specification) 

**[3 CITS SIARD Requirements](#3-cits-siard-requirements)** 

> [3.1 Folder structure and example](#31-folder-structure-and-example) 
>
> [3.2 Package and Representation
> METS](#32-package-and-representation-mets) 
>
> [3.3 Package METS requirements](#33-package-mets-requirements) 
>
> [3.4 Representation METS
> requirements](#34-representation-mets-requirements) 
>
> [3.5 METS requirements between Package and
> Representation](#35-mets-requirements-between-package-and-representation)
>
>
> [3.6 {SIARD_1.0, SIARD2.0, SIARD2.1} --
> requirements](#36-siard_10-siard20-siard21--requirements) 
>
> [3.7 {Database_dump} -- requirements](#-37database_dump-requirements) 

> [3.8 {SIARD_lobs} -- requirements](#38-siard_lobs--requirements) 

**[4 SIP requirements](#4-sip-requirements)** 

> [4.1 Submission Agreement
> requirements](#41-submission-agreement-requirements) 

**[5 AIP requirements](#5-aip-requirements)** 

**[6 DIP requirements](#6-dip-requirements)** 

**[7 Documentation requirements](#7-documentation-requirements)** 

**[Glossary](#glossary)** 

**[Postface](#postface)** 

**LIST OF FIGURES**

Figure 1: Layered Data Model

Figure 2: Information Package structure 9




## 2 Context


### 2.1 Purpose

The purpose of this document is to describe the Content Information Type Specification for Relational Databases (RDB) using the format Software Independent Archiving of Relational Databases (SIARD). The specification is designed to be used for the transfer to and from archives. This specification is supported by an XML-schema and a Schematron document which includes rules that the XML-schema cannot validate. 


### 2.2 Layered data model

This section introduces the structure of the data model, which is based on a layered approach for information package definitions (Figure 1). The Common Specification for Information Packages (CSIP) forms the outermost layer. The general SIP, AIP and DIP specifications add, respectively, submission, archiving and dissemination information to the CSIP specification. The third layer of the model represents specific content information type specifications, such as this CITS SIARD specification. Additional layers for business-specific specifications and local variant implementations of any specification can be added. 

 ![](pictures/Data_Model_Structure.png)

<a name="fig1"></a>
**Figure 1: Data Model Structure** 

Every level in the data model structure inherits metadata entities and elements from the higher levels. In order to increase adoption, a flexible schema has been developed. This will allow for extension points where the schema in each layer can be extended to accommodate additional information on the next specific layer until, finally, the local implementation can add specific entities or metadata elements to satisfy very specific local needs. Extension points can be implemented by:



*   Embedding foreign extension schemas (in the same way as supported by METS [[http://www.loc.gov/standards/mets/](http://www.loc.gov/standards/mets/)] and PREMIS [[http://www.loc.gov/standards/premis/](http://www.loc.gov/standards/premis/)]). These support both increasing the granularity of existing metadata elements by using more detailed data structures as well as adding new types of metadata.
*   Substituting metadata schemas for standards more appropriate for the local implementation.  

The structure allows the addition of more detailed requirements for metadata entities, for example by:



*   Increasing the granularity of metadata elements by using more detailed data structures, or 
*   Adding local controlled vocabularies.

For consistency, design principles are reused between layers as much as possible.


### 2.3 The boundaries of this specification and the SIARD-specification

SIARD is an independent format for archiving relational databases and hence has its own specification ([https://github.com/DILCISBoard/SIARD](https://github.com/DILCISBoard/SIARD)) but there are areas where the SIARD specification deliberately states that packaging of the SIARD-file among other aspect is outside the scope of the SIARD specification:


>“It should be noted that the SIARD format is only the long-term storage format for a specific type of digital documents (relational databases) and is therefore designed entirely independently of package structures such as the SIP (Submission Information Package), AIP (Archival Information Package) and DIP (Dissemination Information Package) in the OAIS model. It is assumed that a database in SIARD format is archived as part of such an information package together with other documents (externalized large object files, translation maps for external file names, database documentation, business documents relevant to the understanding of the database, etc.).” -
 SIARD 2.1.1, p. 7

This CITS SIARD specification describes how to package SIARD-files and any accompanying external LOBs in CSIP package(s). This specification also describes how to package extra metadata and context documentation so that long term preservation and dissemination can take place. 

As in all classification issues it is important to have collectively exhaustive and mutually exclusive categories and even though the SIARD specification deliberately states that package structures are not part of the specification then there are circumstances and scenarios where it is not clear whether an issue falls under the scope of a specification like this one or under the scope of the SIARD specification itself.  

This CITS SIARD specification has been written during the eArchiving building block in the two-year E-ARK3-project and during this period the project participants have been struggling with issues that lie in the grey area between the two specifications.  In the E-ARK3-project the project participants have decided to create a Request For Comments (RFC) for an update to the SIARD specification which concentrates on large databases and external lobs. This CITS SIARD specification is therefore dependent on the outcome of that RFC and has been written as if the RFC has been adopted into the SIARD specification.




## 3 CITS SIARD Requirements


###   3.1 Folder structure and example

A visualisation of an example of a valid CITS SIARD-package is illustrated in Figure 2. The example and other examples can also be found as downloadable packages at this link: [https://github.com/DILCISBoard/SIARD-CITS/tree/master/examples](https://github.com/DILCISBoard/SIARD-CITS/tree/master/examples). The example is an information package where a database has LOBs that resides outside the .siard-file. See LOB details under section [3.8 {SIARD_lobs} -- requirements](#38-siard_lobs--requirements)


 ![](pictures/Information_Package_folder_structure.png)


**Figure 2: Information Package folder structure**


### 3.2 Package and Representation METS

A CSIP can consist of zero to many representations, and this is an important feature that needs to be taken into consideration when packing SIARD files within CSIPs. 

There can easily be different representations of the same database located within one CSIP. For example, one package could consist of:



*   one representation where the native proprietary dump is located; 
*   one representation with SIARD-file that conforms only to an older version of the SIARD specification; 
*   one representation with the newest version of the SIARD specification; 
*   one representation where database normalization and/or other dissemination tasks have taken place. 

There can be several DIP representations.  There can also be other databases and for example geodata within the same package. 

As for this specification there always needs to be a minimum of one representation and therefore a minimum of two METS.xml. The Package METS.xml has to be a general METS.xml describing if the package itself is mainly a CITS_SIARD package, and then the single representations need to describe what specific SIARD versions they consist of. 


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_1</td>
		<td></td>
		<td>There <b>MUST</b> be minimum one representation and therefore minimum one Package METS.xml and minimum one Representation METS.xml in a CITS SIARD package.</td>
		<td>1..1 MUST </td>
	</tr>
</tbody>
</table>



### 3.3 Package METS requirements


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and
Location</th>
		<th>Description
and Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_2 Ref CSIP2 </td>
		<td>Type mets/@TYPE </td>
		<td>For information packages that primarily contain relational databases the value in Package mets/@TYPE <b>MUST</b> be &quot;Databases&quot; as taken from the CSIP Vocabulary for Content Category.</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_3 Ref CSIP4 </td>
		<td>Content Information Type Specification mets/ @csip:CONTENTINFORMATIONTYPE </td>
		<td>For information packages that primarily contain relational databases the value in Package mets/ @csip:CONTENTINFORMATIONTYPE <b>MUST</b> be &quot;CITS_SIARD&quot; as taken from the CSIP Vocabulary for Content Information Type.</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_4 Ref CSIP5 </td>
		<td>Other Content Information Type Specification mets/@csip :OTHERCONTENTINFORMATIONTYPE </td>
		<td>For information packages that primarily contain relational databases the Package METS must <b>NOT</b> have a mets/@csip :OTHERCONTENTINFORMATIONTYPE</td>
		<td>0..0 NOT </td>
	</tr>
	<tr>
		<td>SIARD_5 Ref CSIP6 </td>
		<td>METS Profile mets/@PROFILE </td>
		<td>For information packages that primarily contain relational databases the value in the @PROFILE <b>MUST</b> be &quot;https: //SIARD.dilcis .eu/profile/CI TS_SIARD.xml&quot;</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_6 Ref CSIP62 </td>
		<td>fileSec Representation Content Information Type Specification mets/file Sec/fileGrp[ @USE=&#39;Representations&#39;]/ @csip:CONTENTINFORMATIONTYPE </td>
		<td>There <b>MUST</b> be a minimum of one mets/file Sec/fileGrp[ @USE=&#39;Representations&#39;]/ @csip:CONTENTINFORMATIONTYPE with the value &quot;CITS_SIARD&quot; as taken from the CSIP Vocabulary for Content Information Type that direct to the representation METS.xml in the representation containing a relational database.</td>
		<td>1..n MUST </td>
	</tr>
	<tr>
		<td>SIARD_7 Ref CSIP63 </td>
		<td>fileSec Other Content Information Type Specification mets/fileSec/fileGrp[@cs ip:CONTENTINFORMATIONTYPE=&#39; CITS_SIARD &#39;]/@csip :OTHERCONTENTINFORMATIONTYPE </td>
		<td>For any mets/file Sec/fileGrp[ @csip:CONTENTINFORMATIONTYPE with the value &quot;CITS_SIARD&quot; there <b>MUST</b> be a @csip :OTHERCONTENTINFORMATIONTYPE attribute with a value taken from the vocabulary {SIARD_1.0; SIARD_2.0, SIARD_2.1, D atabase_dump}.</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_8 Ref C SIP105-CSIP112 </td>
		<td>StructMap METS pointer </td>
		<td>For any fileGrp/ @csip:CONTENTINFORMATIONTYPE with the value &quot;CITS_SIARD&quot; there <b>MUST</b> be a corresponding @div- representation in the StructMap-element</td>
		<td>1..1 MUST </td>
	</tr>
</tbody>
</table>


Example 1: Package METS element example.


```



```



### 3.4 Representation METS requirements



<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and
Location</th>
		<th>Description
and Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_9 Ref CSIP2 </td>
		<td>Type mets/@TYPE </td>
		<td>For representations that primarily contain relational databases the value in Package mets/@TYPE <b>MUST</b> be &quot;Databases&quot; as taken from the CSIP Vocabulary for [Content Category] .</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_10 Ref CSIP4 </td>
		<td>Content Information Type Specification mets/ @csip:CONTENTINFORMATIONTYPE </td>
		<td>For representations that primarily contain relational databases and that conforms to CITS SIARD the value in Package mets/ @csip:CONTENTINFORMATIONTYPE <b>MUST</b> be &quot;CITS_SIARD&quot; as taken from the CSIP Vocabulary for [Content Information Type] .</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_11 Ref CSIP5 </td>
		<td>Other Content Information Type Specification mets/@csip :OTHERCONTENTINFORMATIONTYPE </td>
		<td>For representations where mets/ @csip:CONTENTINFORMATIONTYPE has the value &quot;CITS_SIARD&quot; then mets/@csip :OTHERCONTENTINFORMATIONTYPE <b>MUST</b> have a value taken from the vocabulary {SIARD_1.0; SIARD_2.0, SIARD_2.1, Database_dump}</td>
		<td>0..0 NOT </td>
	</tr>
	<tr>
		<td>SIARD_12 Ref CSIP6 </td>
		<td>METS Profile mets/@PROFILE </td>
		<td>For information packages that primarily contain relational databases the value in the @PROFILE <b>MUST</b> be &quot;https:/ /SIARD.dilcis. eu/profile/CIT S_SIARD_repres entation.xml&quot;</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_13 Ref CSIP64-CSIP79 </td>
		<td>File Pointer fileSec/file Grp/file@csip :OTHERCONTENTINFORMATIONTYPE </td>
		<td>If the value in mets/@csip :OTHERCONTENTINFORMATIONTYPE is {SIARD_1.0, SIARD2.0, SIARD2.1, Database_dump} then there <b>MUST</b> exist one and only one file in the fileGrp with @USE = &quot;data&quot; with an identical value in fileSec/file Grp/file@csip :OTHERCONTENTINFORMATIONTYPE that is used to locate the relevant database file.</td>
		<td>1..1 MUST </td>
	</tr>
</tbody>
</table>




### 3.5 METS requirements between Package and Representation
<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_14</td>
		<td>Typemets/@TYPE</td>
		<td>If the value in representation mets/@csip:OTHERCONT ENTINFORMATIONTYPE is {SIARD_1.0, SIARD2.0, SIARD2.1, Database_dump} then the Package METS.xml fileGrp who refers to the Package METS.xml <b>MUST</b> have the same value.</td>
		<td>1..1MUST</td>
	</tr>
</tbody>
</table>



### 3.6 {SIARD_1.0, SIARD2.0, SIARD2.1} – requirements


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_15 </td>
		<td> </td>
		<td>If the value in mets/@csip:OTHERCONT ENTINFORMATIONTYPE is {SIARD_1.0, SIARD2.0, SIARD2.1} then there <b>MUST</b> exist a file named [databaseName].siard in Representations/[RepresentationName]/data</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_16 </td>
		<td> </td>
		<td>The SIARD version of the SIARD-file <b>MUST</b> be the same as the version provided in mets/@csip:OTHERCONT ENTINFORMATIONTYPE and fileSec/fileGrp/fi le@csip:OTHERCONT ENTINFORMATIONTYPE</td>
		<td>MUST </td>
	</tr>
	<tr>
		<td>SIARD_17 </td>
		<td> </td>
		<td>The representati ons/[RepresentationName]/data/[databaseName].siard <b>SHOULD</b> be a valid SIARD file</td>
		<td>SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_18 </td>
		<td> </td>
		<td>There <b>SHOULD</b> be minimum one validation report in the documentation folder for the validation of the SIARD-file</td>
		<td>1..n SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_19 </td>
		<td> </td>
		<td>The file name of the SIARD file representati ons/[RepresentationName]/data/[databaseName].siard <b>MAY</b> be the short database identifier of the database as specified in the &lt;dbname&gt; element of the metadata.xml file in the SIARD file but it is not recommended.</td>
		<td>MAY </td>
	</tr>
</tbody>
</table>



### 3.7 {Database_dump} – requirements


For authenticity and possible dissemination purposes, the OAIS might want to have a representation with a proprietary database dump from the original database management system.


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_20 </td>
		<td> </td>
		<td>If the value in mets/@csip:OTHERCONTENTINFORMATIONTYPE is &quot;Database_dump&quot; then there <b>MUST</b> exist a proprietary database dump in Representations/[RepresentationName]/data</td>
		<td>1..1 MUST </td>
	</tr>
	<tr>
		<td>SIARD_21 </td>
		<td> </td>
		<td>There <b>SHOULD</b> be preservation metadata describing the proprietary database dump</td>
		<td>1..n SHOULD </td>
	</tr>
</tbody>
</table>



### 3.8 {SIARD_lobs} – requirements

A relational database can consist solely of table data, but it can as easily have large objects (LOBs). Large object (LOB) is the common description for large character content (CLOB) or large binary (BLOB) content - such as video, sound, images, word processing documents etc.

These LOBs can be stored inside a relational database as CLOBs or BLOBs within cells or outside as external files - also called external LOBs (SQL/MED). 

In the SIARD specification from SIARD2.0 and onwards the external LOBs can be placed outside the table data within the folder structure in the .siard-file or they can be placed outside the .siard-file. As stated in the scope of this specification there is work being done to create a RFC to the SIARD specification that handles large databases and LOBs. 


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_22 </td>
		<td> </td>
		<td>If a database has LOBs outside the .siard-file then these <b>SHOULD</b> be stored in the same representation as the .siard-file</td>
		<td>SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_23 </td>
		<td> </td>
		<td>LOBs <b>MAY</b> be stored in its own representation, and the value in mets/@csip:OTHERCONTENTINFORMATIONTYPE is &quot;SIARD_lobs&quot;. For storage and preservation actions the OAIS can decide to handle LOBs in its own representation. This way there can be different representations of .siard-files that link to the same lob-representation. The complexity rises by choosing this solution and the CSIP states: &quot;Representation level METS files should not reference files outside of their representation&quot;. It therefore has to be a deliberate choice to allow this way of handling LOBs</td>
		<td>MAY </td>
	</tr>
</tbody>
</table>



## 4 SIP requirements


### 4.1 Submission Agreement requirements

There should be a submission agreement in the SIP representation that has been tailored to handle preservation of relational databases. Since no standard for submission agreements for databases exist yet, the following requirements are not yet able to be automatically validated at this specification level. It is up to the business specific specification layer or local implementation layer (see 1.2 Layered Data Model) to set up requirements that can be automatically validated.


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_23 </td>
		<td> </td>
		<td>There <b>SHOULD</b> be a submission agreement in the SIP representation that has been tailored to handle preservation of relational databases</td>
		<td>1..1 SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_24 </td>
		<td> </td>
		<td>The submission agreement <b>SHOULD</b> describe how many representations of the database that the Producer has to submit.</td>
		<td>0..1 SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_25 </td>
		<td> </td>
		<td>The submission agreement <b>SHOULD</b> describe whether the submitted representations of a database is 1:1 with the running database (Full SIARD export) or if any alterations have been made (only a subset of tables)</td>
		<td>0..1 SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_26 </td>
		<td> </td>
		<td>The submission agreement <b>SHOULD</b> list the tables that are required to be submitted to the archive and to be preserved.</td>
		<td>0..1 </td>
	</tr>
	<tr>
		<td>SIARD_27 </td>
		<td> </td>
		<td>The submission agreement <b>SHOULD</b> list a set of SQL queries that are decided to be submitted to the archive and are to be preserved under the &lt;views&gt;-element in metadata.xml. The SQL queries <b>SHOULD</b> provide the most useful queries in the database for designated communities.</td>
		<td>0..1 SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_28 </td>
		<td> </td>
		<td>The submission agreement <b>SHOULD</b> list the documentation that is decided to be submitted to the archive. See [[7 Documentation requirements ]{.ul}](#7-documentation-requirements)</td>
		<td>0..1 SHOULD </td>
	</tr>
</tbody>
</table>


 


## 5 AIP requirements

None yet.


## 6 DIP requirements

None yet.


## 7 Documentation requirements

There should be documentation in the representations and/or in the information package. Since no standard for documentation of databases exists yet, the following requirements are not yet able to be automatically validated at this specification level. It is up to the business specific specification layer or local implementation layer (see 1.2 Layered Data Model) to set up requirements that can be automatically validated. 


<table>
<thead>
	<tr>
		<th>ID</th>
		<th>Name and Location</th>
		<th>Description and
Usage</th>
		<th>Card &amp; Level</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>SIARD_29 </td>
		<td> </td>
		<td>Tables, coulumns/fields, keys, coded values SHOULD be explained, preferably in the metadata.xml and via code tables or the SIARD file or alternatively in the Documentation folder.</td>
		<td>1..n SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_30 </td>
		<td> </td>
		<td>There <b>SHOULD</b> be a system diagram in the Documentation folder. Preferably an Entity/Relationship Diagramme</td>
		<td>1..n SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_31 </td>
		<td> </td>
		<td>The (main) system-user dialogues <b>SHOULD</b> be documented, down to the identification of the database coulumns/fields involved in the dialogues, documented as a combination of: 
		<ul>
<li><p>Screenshots, annotated with coulumn/field descriptions, stored in the Documentation folder.</p></li>
<li><p>User documentation describing the system-user dialogue, stored in the Documentation folder.</p></li>
<li><p>If views are not present, additional descriptions of the system (application) logic, stored in the Documentation folder.</p></li>
</ul>
	<td>1..n SHOULD </td>
	<tr>
		<td>SIARD_32 </td>
		<td> </td>
		<td>Documentation of the legal context of the database and associated system <b>SHOULD</b> be provided in the Documentation folder.</td>
		<td>1..n SHOULD </td>
	</tr>
	<tr>
		<td>SIARD_33 </td>
		<td> </td>
		<td>There <b>MAY</b> be videos or screen dumps from the system as seen from the user&#39;s point of view in the Documentation folder.</td>
		<td>1..n SHOULD </td>
	</tr>
    </thead>        
</table>

<br/>

## Glossary

**Table 2: Glossary**


<table>
  <tr>
   <td><strong>Name</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td><strong>Content Information Type (CIT)</strong>
   </td>
   <td>A type of a set of information that is the original target of preservation or that includes part or all of that information. It is an Information Object composed of its Content Data Object and its Representation Information.
   </td>
  </tr>
  <tr>
   <td><strong>DBMS</strong>
   </td>
   <td>Database Management System
   </td>
  </tr>
  <tr>
   <td><strong>OAIS</strong>
   </td>
   <td>Open Archival Information System
   </td>
  </tr>
  <tr>
   <td><strong>RDBMS</strong>
   </td>
   <td>Relational Database Management System
   </td>
  </tr>
  <tr>
   <td><strong>SIARD</strong>
   </td>
   <td>Software Independent Archival of Relational Databases
   </td>
  </tr>
</table>

 

## Postface


<table>
  <tr>
   <td colspan="2" ><strong>AUTHOR(S)</strong>
   </td>
  </tr>
  <tr>
   <td>Name(s)
   </td>
   <td>Organisation(s)
   </td>
  </tr>
  <tr>
   <td>Phillip Aasvang Tømmerholt
   </td>
   <td>The Danish National Archives
   </td>
  </tr>
  <tr>
   <td>Anders Bo Nielsen
   </td>
   <td>The Danish National Archives
   </td>
  </tr>
  <tr>
   <td>Asbjørn Skjødt
   </td>
   <td>The Danish National Archives
   </td>
  </tr>
  <tr>
   <td>Henrik K. R. Jakobsen
   </td>
   <td>The Danish National Archives
   </td>
  </tr>
  <tr>
   <td>Karin Bredenberg
   </td>
   <td>Kommunalförbundet Sydarkivera
   </td>
  </tr>
  <tr>
   <td>Arne-Kristian Groven
   </td>
   <td>Norwegian National Archives (Akrivverket)
   </td>
  </tr>
</table>

<table>
  <tr>
   <td colspan="2" ><strong>REVIEWER(S)</strong>
   </td>
  </tr>
  <tr>
   <td>Name(s)
   </td>
   <td>Organisation(s)
   </td>
  </tr>
  <tr>
   <td>Janet Anderson
   </td>
   <td>Highbury/DNA
   </td>
  </tr>
  <tr>
   <td>Lauri Ratsep
   </td>
   <td>National Archives of Estonia
   </td>
  </tr>
  <tr>
   <td>Jaime Kaminski
   </td>
   <td>Highbury/DNA
   </td>
  </tr>
  <tr>
   <td>Thomas Bolbroe
   </td>
   <td>The Danish National Archives
   </td>
  </tr>
   </td>
  </tr>
</table>

<table>
  <tr>
   <td colspan="3" ><strong>Project co-funded by the European Commission within the ICT Policy Support Programme</strong>
   </td>
  </tr>
  <tr>
   <td colspan="3" ><strong>Dissemination Level</strong>
   </td>
  </tr>
  <tr>
   <td><strong>P</strong>
   </td>
   <td><strong>Public</strong>
   </td>
   <td>x
   </td>
  </tr>
  <tr>
   <td><strong>C</strong>
   </td>
   <td><strong>Confidential, only for members of the Consortium and the Commission Services</strong>
   </td>
   <td>
   </td>
  </tr>
</table>

 


**<span style="text-decoration:underline;">REVISION HISTORY AND STATEMENT OF ORIGINALITY</span>**

**Submitted Revisions History**


<table>
  <tr>
   <td><strong>Revision No.</strong>
   </td>
   <td><strong>Date</strong>
   </td>
   <td><strong>Authors(s)</strong>
   </td>
   <td><strong>Organisation</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>[Version]
   </td>
   <td>[Date]
   </td>
   <td>[Who]
   </td>
   <td>[Affiliation]
   </td>
   <td>[What]
   </td>
  </tr>
  <tr>
   <td>1.0
   </td>
   <td>14-08-2020
   </td>
   <td>Phillip Aasvang Tømmerholt
   </td>
   <td>Danish National Archives
   </td>
   <td>DRAFT version for internal review
   </td>
  </tr>
  <tr>
   <td>1.1
   </td>
   <td>31-08-2020
   </td>
   <td>Phillip Aasvang Tømmerholt
   </td>
   <td>Danish National Archives
   </td>
   <td>DRAFT version with changes based on internal review
   </td>
  </tr>
  <tr>
   <td>1.2
   </td>
   <td>29-09-2020
   </td>
   <td>Phillip Aasvang Tømmerholt
   </td>
   <td>Danish National Archives
   </td>
   <td>Included Layered Data Model and Documentation requirements
   </td>
  </tr>
</table>


