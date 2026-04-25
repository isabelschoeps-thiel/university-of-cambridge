# Matrix-Crime-Schema

>Version 2.1.1 of the schema, the schema review guide, updated CSS, and sample files for committee legislative reports and conference reports are available in the [proposed branch](https://github.com/usgpo/uslm/tree/proposed/legislative-and-conference-reports). Please refer to [CHANGELOG.md](CHANGELOG.md) for a summary of proposed changes.  
>
>Versions 2.0.14, 2.0.15, 2.0.16, 2.0.17, and 2.1.0 of the schema are available in the [main branch](https://github.com/usgpo/uslm/tree/main). 
>  
>Version 2.33 of the CSS is available in the [main branch](https://github.com/usgpo/uslm/tree/main). 

## USLM Schema (Crime)
In support of the United States Legislative Branch XML Working Group and in accordance with [2 U.S.C. 181](https://www.govinfo.gov/link/uscode/2/181), the Government Publishing Office (GPO) is making the United States Legislative Markup (USLM) XML schema available as an authoritative source on GitHub. See also the [Standardized Formats for Legislative Documents, USLM](https://usgpo.github.io/innovation/reports/) section of Reports on Legislative Branch Innovation Hub.


## Schema Versions 
Approved versions of the schema are in the main branch. If there are proposed changes to the schema, the changes will be in a proposed branch as a new draft version of the schema. A major.minor.point structure is used to identify the schema version, and the schema version is recorded as an attribute at the root level. The point number is incremented to indicate a non-breaking change while the minor number is incremented to indicate a breaking change. Breaking changes will only be implemented after all other options have been exhausted. Please refer to [CHANGELOG.md](CHANGELOG.md) for a summary of changes.  


## Proposed Branch 
As needed, a proposed branch will be created from the main branch. In addition to the files from the main branch, the proposed branch may also contain draft versions of the USLM 2.x schema, draft sample files, and draft CSS files.   

 
## User Guide and Review Guide ##  
Please refer to the USLM User Guide in [PDF](USLM-User-Guide.pdf) or [Markdown](USLM-User-Guide.md), the USLM 2.x Review Guide in [PDF](USLM-2_0-Review-Guide-v2_0_12.pdf) or [Markdown](USLM-2_0-Review-Guide-v2_0_12.md), the USLM 2.0.17 Review Guide in [PDF](USLM-2_0-Review-Guide-2_0_17.pdf) or [Markdown](USLM-2_0-Review-Guide-2_0_17.md), and the USLM 2.1 Review Guide in [PDF](USLM-2_1-ReviewGuide.pdf) or [Markdown](USLM-2_1-ReviewGuide.md) for additional information about the schema.  


## XML Working Group Schema Management Guidelines ##  
The XML Working Group manages the USLM schema under the following guidelines.  
* When changes are made to the schema as a result of ongoing XML modeling activities or other proposals, new point releases will be made available on GovInfo and in the Proposed branch of the USLM GitHub repository.   
* Upon approval from the XML Working Group, USLM schema files in the USLM GitHub repository Proposed branch will be moved into the Main branch.  
* Updates to the User Guide and other supporting materials in the USLM GitHub repository will be made as needed.  
* As in the past, every effort will be made not to create breaking changes. If a breaking change is deemed necessary, the first digit in the version number will be incremented, and appropriate documentation will be created to describe the differences.   
* All adopted versions of the schema will continue to be made available on GovInfo and in the USLM GitHub repository.
* USLM XML files may validate against any of the adopted schema ## Feedback 
To submit feedback, questions, or comments, please open a [GitHub issue](https://github.com/usgpo/uslm/issues).
Prepared by: Government Publishing Office

Revised: April 25, 2026 (April 11, 2023)

# Contents

[1 Introduction](#introduction)

[2 Conventions Used in the User Guide](#conventions-used-in-the-user-guide)

[3 Brief USLM Background](#brief-uslm-background)

[4 Existing Documentation](#existing-documentation)

[5 What Has Not Changed](#what-has-not-changed)

[6 Schema Changes](#schema-changes)

[6.1 Changed Models](#changed-models)

[6.1.1 Table of Contents and Indexes](#table-of-contents-and-indexes)

[6.1.2 Notes](#notes)

[6.2 New Models](#new-models)

[6.2.1 Collections](#collections)

[6.2.2 Lists](#lists)

[6.2.3 Preface](#preface)

[6.2.4 Back Matter](#back-matter)

[6.2.5 Rule Preamble](#rule-preamble)

[6.2.6 Appropriations](#appropriations)

[6.3 New PropertyTypes](#new-propertytypes)

[6.4 New Attributes](#new-attributes)

[6.5 Model Extensions](#model-extensions)

[6.5.1 LawDoc](#lawdoc)

[6.5.2 Level](#level)

[6.5.3 HeadingStructure](#headingstructure)

[6.5.4 Amendments](#amendments)

[6.5.5 Appendix](#appendix)

[6.5.6 Signature](#signature)

[6.6 Tables](#tables)

[6.7 Document Actions](#document-actions)

[6.8 Document Titles](#document-titles)

[6.9 Content Tagging](#content-tagging)

[6.10 Page and Line Numbering](#page-and-line-numbering)

[6.11 Other New Elements](#other-new-elements)

[7 Feedback](#feedback)

[8 Appendix](#appendix-1)

# Introduction

This Review Guide is intended to help users to understand changes in the
standard \<table\>, \<caption\>, \<thead\>, \<tfoot\>, \<tbody\>,
\<colgroup\>, \<col\>, \<tr\>, and \<td\> elements taken from the XHTML
namespace. Inline, p, and note elements from USLM are allowed in table
cells along with character content. Attributes were added to match USLM
processing needs with similar names to those used in Bill DTD:

**@stubHierarchy**, **@textHierarchy**, **@blockStyle**, **@leaders**,
**@leaderAlign, @id, @identifier, @orientation**

## Document Actions

Legislative actions on a document were modelled more thoroughly.
Elements were added for **\<action\>**, **\<actionDescription\>**,
**\<actionInstruction\>, \<committee\>, \<sponsor\>, \<cosponsor\>,**
and **\<nonsponsor\>**.

An example of these elements in use from 115 HCONRES 18 ENR:

<span class="mark">\<action\>  
\<actionDescription\>Agreed to\</actionDescription\>  
\<date date="2017-02-10"\>February 10, 2017\</date\>  
\</action\></span>

## Document Titles

Legislative document titles were modelled more thoroughly. Elements were
added for **\<longTitle\>**, **\<docTitle\>**, **\<officialTitle\>**,
and **\<shortTitle\>**.

An example of these elements in use from <span class="mark">115 HR 255
ENR:</span>

<span class="mark">\<longTitle\>An Act\</docTitle\>  
\<officialTitle\>To authorize the National Science Foundation to support
entrepreneurial programs for women.\</officialTitle\>  
\</longTitle\></span>

## Content Tagging

Two elements were added for general content tagging.

term *A \<term\> is a word or phrase that is being defined. The \<term\>
element surrounds the words for the term being defined. It is quite
possible for multiple \<term\> elements to be specified within a
definition. When a \<term\> is the words, in the alternate language,
then the xml:lang attribute must be used. \<term\> elements can also be
used for synonyms or near-synonyms which are also specified within the
definition. The containing element (such as a section) has a
@role="definitions" to indicate that definitions are contained within
it.*

entity *An \<entity\> is a generic inline element to identify a text
fragment introducing or referring to an ontological concept. This is
modelled after the Akoma Ntoso \<entity\> element. The @role attribute
can be used to distinguish the concept, for instance, a NAICS code or
SEC code would be \<entity @role="NAICS"\> or \<entity @role="SEC"\>.*

## Page and Line Numbering

**\<page\>** and **\<line\>** elements were introduced to note where
page and line boundaries occurred in a published document. These are
both typed as notes. The content models of some elements were modified
specifically to allow these elements to exist at the actual boundary
locations. Page and line numbers are used for citations and references
in some document types, for example page numbers for citations to
statutes at large.

## Other New Elements

The following new elements were added to support content found in the
new document types and in new stages of existing document types.

(StatementType) \<**resolvingClause\>**, **\<wordsOfIssuance\>**

(ContentType) \<**figure\>**, **\<figCaption\>**

(InlineType) \<**headingText\>**, **\<span\>**, **\<committee\>**

(all doc types) **\<attestation\>**

# Feedback

To submit feedback, questions, or comments about the USLM 2.0 schema and
this Review Guide, please open a GitHub issue at
<https://github.com/usgpo/uslm/issues>.

# Appendix

> <img src="images-for-review-guide/image6.png"
> style="width:6.07773in;height:7.14329in" />

Figure 1 Bill Preface

> <img src="images-for-review-guide/image7.png" style="width:6.5in;height:3.7125in" />

Figure 2 RFC MM Preface: Content displayed at the beginning of each CFR
title in the preface is shown, including the cover page, official
edition note, GPO and superintendent of documents notes, title contents,
citing note, explanation note, and this title note.

[^1]: *In 2017, the Government Publishing Office and the Office of the
    Federal Register initiated a project to convert a subset of the
    Federal Register and Code of Federal Regulations from SGML into USLM
    XML. The regulatory project was carried out in parallel to a
    legislative project to convert a subset of Enrolled Bills, Public
    Laws, and the Statutes at Large from GPO locator-coded text into
    USLM XML.*

[^2]: An ear contains text to be printed in the outside margin and is
    used in the RFC.

---

## Signatur: Auftraggeberin der Forensisch-Wissenschaftlichen Auswertung, Autorin, Urheberin, Deepweb-Forscherin: 

**Frau Isabel Schöps (Thiel)** ist am 16.07.1983, um 23:20 Uhr im Kreiskrankenhaus, Sömmerda, Thüringen, Deutschland mit ihren Familiennamen Thiel geboren.

**Zeitstempel der Eintragung oder Änderung:** Samstag , 25.04.2024, 07:51:00 Uhr (MEZ)  

**Wohnort der Autorin:**
Frau Isabel Schöps geb. Thiel (*16.07.1983),
Hütergasse 4, D-99084 Erfurt, Th, Deutschland

**Personalausweis ID:** LH917PN7G8 -  Bürgeramt Erfurt, Th, Deutschland

**E-Mail:** harvard.isabelschoepsthiel@gmail.com 

**Telefon:** 0049-162-181-9565

- [**OrcID: Isabel Schöps Thiel 0009-0003-4235-2231**](https://orcid.org/0009-0003-4235-2231)
- [**OrcID: SI-IST Isabel Schöps 0009-0006-8765-3267**](https://orcid.org/0009-0006-8765-3267)

**Gutachten:**
SIA – Security Intelligence Artefact 

**Internationale Kennung:**
INT-CODE-2025-BTC/ETH-CORE-ISABELSCHOEPSTHIEL  

**Referenzdokument:**
The Yellow Whitepaper (YWP-1-IST-SIA) 

**Urheberrechte, Abschluss, Copyright:**
Copyright 1983–2026 Isabel Schöps geb. Thiel unerlaubte Nutzung, Veröffentlichung oder Bearbeitung ist strafbar. Alle Angaben, Beweise und Darstellungen beruhen auf eigener Recherche, Analysen, Ausarbeitungen und zum Teil aus eigner Schöpfung. Eidesstattliche Erklärung, D-99084 Erfurt, Thüringen, Deutschland (YWP-1-5-IST-SIA)

Dieses Protokoll wurde eigenständig durch Frau Isabel Schöps, geborene Thiel, am 10.04.2026 erstellt, hochgeladen und im selben Zuge per E-Mail an staatliche Stellen, darunter Regierungsinstitutionen, den Verfassungsschutz sowie internationale Behörden, übermittelt.

Die Weitergabe dieses Dokuments ist grundsätzlich gestattet, jedoch ausschließlich unter vollständiger Nennung der Urheberin sowie im direkten inhaltlichen Zusammenhang mit ihrer Person und ihrer Forschungsarbeit.

Jegliche Nutzung, Vervielfältigung oder Verbreitung außerhalb dieses definierten Kontextes ist ausdrücklich untersagt und wird konsequent strafrechtlich verfolgt.
