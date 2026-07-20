# ADR-001: Report Markup Language

## Status

Accepted

## Context

The project requires a human-readable document description language.

## Decision

Use YAML as the serialization format for RML.

## Consequences

### Positive

- Human readable
- Easy to edit
- Widely supported
- Native nested structures

### Negative

- Whitespace sensitive
- More difficult to validate than JSON