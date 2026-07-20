# Report Markup Language (RML)

Version: 1.0

---

## Purpose

The Report Markup Language (RML) is a YAML-based language used by the Report Generator
to describe the logical structure of a report.

RML separates:

- Content
- Document Structure
- Presentation

The report generator is responsible for converting an RML document into a formatted output
such as Microsoft Word (.docx).

## Design Goals

The Report Markup Language (RML) is designed to be:

- Human-readable
- Easy to author manually
- Easy to validate
- Independent of any output format
- Extensible through new block types
- Stable across report templates

## Non-Goals

RML does not attempt to:

- Replace Markdown or HTML
- Describe visual styling
- Define page layouts
- Support every document feature in version 1.0

Each RML document SHOULD declare its schema version.

---

## Terminology

**Document**
A complete report represented by an RML file.

**Section**
A logical division of a document containing related information.

**Block**
The smallest renderable unit within a section.

**Renderer**
A software component responsible for converting a specific block type into the target output format.

**Theme**
Defines the visual appearance of a document.

**Template**
Defines the structural layout of a document.

---

## Design Principles

1. Content must not contain formatting.
2. Themes control appearance.
3. Templates control document layout.
4. RML describes document structure only.
5. Every document is composed of sections.
6. Every section is composed of blocks.
7. Every block has exactly one renderer.

## Root Object

An RML document SHALL contain:

- metadata
- sections

An RML document MAY contain:

- references

## Metadata

Metadata stores information about the report.

Typical fields include:

- title
- subtitle
- author
- institute
- department
- subject
- practical_number
- academic_year
- date

## Sections
Each document contains one or more sections.

Each section contains:

heading

blocks

## Blocks

Every block SHALL define:

- type
- content
- options (optional)

The `type` identifies the renderer responsible for the block.

The `content` stores the logical information represented by the block.

The `options` object contains renderer-specific configuration without affecting the document theme.

## Supported Block Types (Version 1.0)

### Text
- paragraph
- quote

### Lists
- bullet_list
- numbered_list

### Tables
- table

### Figures
- placeholder
- image

### Programming
- code
- terminal

### Structure
- page_break
- horizontal_rule

## Out of Scope (Version 1.0)

The following features are intentionally excluded:

- Mathematical equations
- Mermaid diagrams
- Charts
- Embedded videos
- Interactive content
- Cross-references

## Versioning

RML follows semantic versioning.

Breaking schema changes increment the major version.

New block types increment the minor version.

Clarifications and corrections increment the patch version.