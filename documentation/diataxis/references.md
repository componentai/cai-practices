# Reference Documentation

Summary of [Diátaxis Reference Guide](https://diataxis.fr/reference/)

## What is Reference Documentation?

Reference guides are **technical descriptions** of the machinery and how to operate it. They are **information-oriented** and contain propositional or theoretical knowledge that users consult during their work.

- The purpose is to describe succinctly and in an orderly way
- Content is led by the product it describes (not user needs like tutorials/how-to guides)
- For software: describes APIs, classes, functions, and how to use them
- Provides users with truth, certainty, and confidence to do their work

## Key Characteristics

- **Austere**: One consults reference material, not reads it
- **Authoritative**: No doubt or ambiguity
- **Like a map**: Tells you what you need to know without checking yourself

## Key Principles

### 1. Describe and Only Describe

Neutral description is the key imperative. Avoid:
- Explaining
- Instructing
- Discussing
- Opining

Instead, link to how-to guides, explanations, and tutorials for those purposes.

**Style requirements:**
- Austere and uncompromising
- Neutral, objective, factual
- Structured according to the machinery itself

### 2. Adopt Standard Patterns

Reference material is useful when it is **consistent**. Use standard patterns so users can find information where they expect it, in a familiar format. If you are unsure of the standard pattern, point it out, so `cai-practices` can include the new standard.

### 3. Respect the Structure of the Machinery

The documentation structure should **mirror the product structure**, allowing users to navigate both simultaneously. The logical, conceptual arrangement of the code should help make sense of the documentation.

### 4. Provide Examples

Examples illustrate reference material without becoming distracting. Usage examples are a succinct way to show context without falling into explaining or instructing.

### 5. mkdocstrings Compatibility

Docstrings are auto-rendered via [mkdocstrings](https://mkdocstrings.github.io/). Formatting matters! Ensure docstrings follow Google style consistently so they render correctly in generated documentation.

## Language of Reference Guides

- **State facts** about the machinery and its behaviour
- **List** commands, options, operations, features, flags, limitations, error messages
- **Provide warnings** where appropriate (e.g., "You must use X", "Never do Y")

## See Also

For documenting functions that use Foreign Function Interface (FFI) bindings to other languages (Futhark, Rust, CUDA, etc.), see [FFI Documentation](../guides/ffi.md).
