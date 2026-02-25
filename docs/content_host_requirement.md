# PCA Host Content Requirements  
*Information requirements ensuring cost-efficient & quality publication of content*

---

## Table of contents
- [Introduction](#introduction)
- [Scope, assumptions, and terminology](#scope-assumptions-and-terminology)
- [R0. Parsing, syntax, and file-level constraints](#r0-parsing-syntax-and-file-level-constraints)
- [R1. Ontology declaration and metadata](#r1-ontology-declaration-and-metadata)
- [R2. Prefix declarations ](#r2-prefix-declarations)
- [R3. Public visibility](#r3-public-visibility)
- [R4. Namespace governance and ownership](#r4-namespace-governance-and-ownership)
- [R5. Namespace structure and IRI patterns](#r5-namespace-structure-and-iri-patterns)
- [R6. Term-level metadata](#r6-term-level-metadata)
- [R7. Declaring dependencies](#r7-declaring-dependencies)
- [R8. Resource typing](#r8-resource-typing)
- [R9. Instance data / reference datasets](#r9-instance-data-and-reference-datasets)

---

## Introduction
This document describes the publication policy for PCA ontologies and content hosted through PCA’s platform. Given fulfillment of all requirements, PCA is able to give a price guarantee for publishing and hosting your ontology. For comments, questions, or feedback, contact info@posccaesar.org.

---

## Scope, assumptions, and terminology

### Scope
This document defines requirements for publishing ontologies, reference data, and related RDF content in the PCA platform.

### Assumptions
- Content is delivered as RDF in Turtle format.  
- Each file produces exactly one RDF graph.  
- Each file represents a single ontology.

### Terminology
- **File** – a single Turtle (`.ttl`) file producing exactly one RDF graph.  
- **Ontology** – an RDF graph declared as `owl:Ontology`, representing a coherent conceptual model and governance boundary, including its namespace.  
- **Published resource** – any RDF resource intended to be indexed, validated, visualized, or reused via the PCA platform (classes, properties, shapes, instances, etc.).  
- **Namespace** – the IRI space governed by an ontology owner for minting resources.  
- **Instance data (reference data)** – RDF individuals published as part of an ontology.  

### Normative keywords
The following verbal forms are interpreted in accordance with ISO/IEC Directives, Part 2:

- **shall** — requirement  
- **shall not** — prohibition  
- **should** — recommendation  
- **may** — permission  

---

## R0. Parsing, syntax, and file-level constraints

### R0.1 Turtle syntax
- The file **shall** be valid Turtle (`.ttl`) and parse without errors.  
- The file **shall** be directly machine-processable without preprocessing.

### R0.2 Encoding
- The file **shall** be encoded in UTF-8.

### R0.3 Graph model
- The file **shall** produce exactly one RDF graph.  
- TriG graphs **shall not** be used.

### R0.4 IRIs and blank nodes
- All published resources **shall** use absolute IRIs.  
- Blank nodes **shall** be internal structural nodes attached to declared named resources, e.g. OWL restrictions, SHACL property-shape structures, RDF lists, or similar anonymous helper nodes.
- Blank nodes **shall not** be used as published first-class resources.

---

## R1. Ontology declaration and metadata

### R1.1 Single ontology
- The file **shall** contain exactly one subject typed as `owl:Ontology`.

### R1.2 Ontology IRI
- The ontology IRI **shall** be an absolute HTTPS IRI under `https://posccaesar.org/`.  
- The ontology IRI **shall** be unique and **shall not** already exist.

### R1.3 Ontology labels and description
- The ontology **shall** have a human-readable title.
    - The title **shall** be expressed using `skos:prefLabel` and/or `rdfs:label`.  
- The ontology **shall** include a human-readable description. 
    - The description **shall** be expressed using `skos:definition`.
    - The description **may** in addition be expressed using `rdfs:comment`.

### R1.4 Versioning
- The ontology **may** declare one `owl:versionIRI`.  
- If declared, the ontology **shall** declare one `owl:versionInfo`.

### R1.5 Ontology self-reference
- The ontology **shall** include `rdfs:isDefinedBy <ontologyIRI>`.
- The `<ontologyIRI>` **may** point to the ontology declared in the file, or another 

---

## R2. Prefix declarations
- If prefixes are used, each **shall** be declared in the file.
- Full IRIs **may** be used.
- Prefixes **shall** be unique and unambiguous.

---

## R3. Public visibility
Every published resource **shall** include `rdfs:isDefinedBy <ontologyIRI>`

Failure to meet this requirement results in published resources not being presented and defined as part of the ontology.

---

## R4. Namespace governance and ownership

### R4.1 Ownership rule
- The file **shall not** assert new facts about resources in namespaces not owned by PCA.
- The file **shall not** assert new facts about resources outside the namespace of the ontology declared in it.
- External ontologies **shall not** be modified by adding triples with their IRIs as subjects.
- E.g. "You cannot add more meaning to an entity belonging to the skos ontology as you are not the author of it."

### R4.2 Extension rule
- Extensions of external standards **shall** be expressed using:
  - PCA IRIs  
  - `rdfs:subClassOf`, `rdfs:subPropertyOf`, or equivalent mapping constructs to the external standard 
- Semantic mappings **may** use SKOS/OWL equivalence relations.

---

## R5. Namespace structure and IRI patterns

### R5.1 Namespace compliance options
PCA supports two compliant namespace patterns for ontologies and their published resources.

#### R5.1.1 ISO 23726-1 compliant namespace
- If an ontology is intended to be compliant with ISO 23726-1 (e.g. a domain ontology under ISO 23726-3 – Industrial Data Ontology), the following namespace pattern **shall** be used for the ontology: `https://posccaesar.org/ontology/<ontology_name>/ont/core`
- The namespace for published resources in the ontology **shall** make use of the following namespace pattern: `https://posccaesar.org/ontology/<ontology_name>/rdl/<resource_name>`
- The IRI of each published resource **shall** be unique.

#### R5.1.2 General PCA compliant namespace
- If an ontology is intended to be published at PCA, but not as a domain ontology under ISO 23726-3, then the following namespace pattern **shall** be used for the ontology: `https://posccaesar.org/ontology/<ontology_path>`
- `<ontology_path>`**may** consist of just the name of the ontology or a more compound path to the ontology.
- The namespace for published resources in the ontology **shall** make use of the following namespace pattern: `https://posccaesar.org/ontology/<ontology_path>/<local_name_path>`
- The `<local_name_path>` **may** contain the name of the sources or a more compooun path.
- The IRI of each published resource **shall** be unique.

### R5.2 Forbidden patterns
- Opaque or hash-based namespaces **shall not** be used.

---

## R6. Term-level metadata

### R6.1 Labels
- Every published resource **shall** have `skos:prefLabel` and/or `rdfs:label`.

### R6.2 Definition
- Every published resource **shall** have `skos:definition`, and **may** additionally have `dcterms:description` and `rdfs:comment`.

### R6.3 Language tags
- Language tags **shall** be valid BCP-47.  
- At most one language per predicate per resource is supported at this time.

---


## R7. Declaring dependencies
- External ontologies **shall** be declared using `owl:imports` if used as dependencies. 

---

## R8. Resource typing
All published resources **shall** be typed according to either:
- A known accessible ontology/vocabulary (e.g. SKOS, OWL, dcterms, rdf, rdfs, any ontology hosted at PCA, etc.), OR  
- A type defined locally in the ontology.

To be presented for visitors exploring PCA content in a browser, published resources **shall** be typed as (directly or derivable):
- `owl:Ontology`  
- `owl:Class`  
- `owl:Thing`  
- `owl:ObjectProperty`  
- `owl:DatatypeProperty`  
- `rdfs:Property`  
- `imf:AttributeType`  
- `imf:BlockType`  
- `imf:TerminalType`  

Published resources **may** be typed as other things, but will not be presented visually.

---

## R9. Instance data and reference datasets
- Instance data is supported.  
- Instance data **shall** follow the same requirements as the other resources described here.