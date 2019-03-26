What is MR\ :sup:`3` \?
=====================================
MR\ :sup:`3` \ (Meta-Model Management based on RDFs Revision Reflection) is an editing tool of RDF-based contents developed for managing a relationship between `RDF (Resource Description Framework) <https://www.w3.org/TR/rdf11-concepts/>`_  and `RDFS (RDF Schema) <https://www.w3.org/TR/rdf-schema/>`_ contents.

Introduction
--------------------
The Semantic Web is one of the most promised candidates as the Web tomorrow, whose basis is on RDF and RDF Schema recommended by the World Wide Web Consortium. The purpose of the idea is to make the data on the Web available not only for displaying but also for automation, integration and reuse of data across various applications. At the moment, a number of supporting environment have been developed as the adopted tools of traditional knowledge engineering based ontologies. These products are mostly concentrating on creating ontologies and managing ontology-based semantic markup. From the standpoint of a significance of information lifecycle on the Semantic Web, in this work, an editing tool of RDF-based contents is developed for managing a relationship between RDF and RDFS contents.

Features
----------------
MR\ :sup:`3` \ provides the three main functions to edit and to manage the several sorts of relationship among RDF and RDFS contents as follows.

Graphical Editing of RDF Descriptions
    Based on the semantics of RDF data model, the tool supports to edit the resource-property-value relation.
Graphical Editing of RDFS Descriptions
    Based on the semantics of RDF Schema model, the tool supports to edit the class-subclass relation and to add the information of properties such as range, domain, sub-property, and so on.
Meta-Model Management Facilities
    In order to reflect the change of RDF or RDFS contents on the other, the tool supports the correspondence between them.

The above function consisted of the following sub-functions.

* Importing an RDF(S) document and editing the RDF(S) data model graphically.
* Exporting an RDF(S) data model as an RDF(S) document based on various formats such as Turtle, JSONLD, RDF/XML, and N-Triples.
* Reflecting changes of RDFS class to RDF resource type.
* Reflecting changes of RDFS property to RDF property.
* Reflecting the change of RDF resource type to the RDFS class and domains and ranges of RDFS property.
* Reflecting changes of RDF property to RDFS property.