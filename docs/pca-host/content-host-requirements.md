---
title: PCA Host Content Requirements
---

_Information requirements ensuring cost-efficient and quality publication of content_

**Note:** This documentation is intended for public consumption and review. Feedback is very welcome, and PCA can incorporate changes iteratively.

## Introduction

This document describes the publication policy for PCA ontologies and content hosted through PCA's platform. Given fulfillment of all requirements, PCA is able to give a price guarantee for publishing and hosting your ontology.

## Scope, assumptions, and terminology

### Scope

This document defines requirements for publishing ontologies, reference data, and related RDF content in the PCA platform.

### Assumptions

- Content is delivered as RDF in Turtle format.
- Each file produces exactly one RDF graph.
- Each file represents a single ontology.

### Terminology

- **File**: a single Turtle (`.ttl`) file producing exactly one RDF graph.
- **Ontology**: an RDF graph declared as `owl:Ontology`, representing a coherent conceptual model and governance boundary, including its namespace.
- **Published resource**: any RDF resource intended to be indexed, validated, visualized, or reused via the PCA platform.
- **Namespace**: the IRI space governed by an ontology owner for minting resources.
- **Instance data (reference data)**: RDF individuals published as part of an ontology.

### Normative keywords

The following verbal forms are interpreted in accordance with ISO/IEC Directives, Part 2:

- **shall**: requirement
- **shall not**: prohibition
- **should**: recommendation
- **may**: permission

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
- Blank nodes **shall** be internal structural nodes attached to declared named resources, for example OWL restrictions, SHACL property-shape structures, RDF lists, or similar anonymous helper nodes.
- Blank nodes **shall not** be used as published first-class resources.

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

## R2. Prefix declarations

- If prefixes are used, each **shall** be declared in the file.
- Full IRIs **may** be used.
- Prefixes **shall** be unique and unambiguous.

## R3. Public visibility

Every published resource **shall** include `rdfs:isDefinedBy`.

Failure to meet this requirement results in published resources not being presented and defined as part of the ontology.

## R4. Namespace governance and ownership

### R4.1 Ownership rule

- The file **shall not** assert new facts about resources in namespaces not owned by PCA.
- The file **shall not** assert new facts about resources outside the namespace of the ontology declared in it.
- External ontologies **shall not** be modified by adding triples with their IRIs as subjects.

### R4.2 Extension rule

- Extensions of external standards **shall** be expressed using PCA IRIs and subclass, subproperty, or equivalent mapping constructs to the external standard.
- Semantic mappings **may** use SKOS or OWL equivalence relations.

## R5. Namespace structure and IRI patterns

PCA supports compliant namespace patterns for ontologies and their published resources. In practice, your ontology and resource IRIs must follow the approved PCA namespace model for either ISO 23726-1-aligned ontologies or general PCA ontologies.

Opaque or hash-based namespaces **shall not** be used.

## R6. Term-level metadata

- Every published resource **shall** have `skos:prefLabel` and/or `rdfs:label`.
- Every published resource **shall** have `skos:definition`, and **may** additionally have `dcterms:description` and `rdfs:comment`.
- Language tags **shall** be valid BCP-47.

## R7. Declaring dependencies

- External ontologies **shall** be declared using `owl:imports` if used as dependencies.

## R8. Resource typing

All published resources **shall** be typed according to either:

- a known accessible ontology or vocabulary
- a type defined locally in the ontology

To be presented for visitors exploring PCA content in a browser, published resources **shall** be typed as, directly or derivably, one of the supported PCA-presentable resource kinds such as ontology, class, property, or selected IMF types.

## R9. Instance data and reference datasets

- Instance data is supported.
- Instance data **shall** follow the same requirements as the other resources described here.

## See also

- [PCA Host](index.md)
- [Get Started with Hosting](get-started-with-hosting.md)
