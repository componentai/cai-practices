# Documentation style guide

**version: 0.1.0**

This style guide for documentation is primarily written for Python, but principles apply to all languages written, if possible.
In this document, "function" means a function, method, generator, or property.

## Principles

We will try to follow [Diátaxis](https://diataxis.fr/) principles and divide documentation up in four distinct parts:

1. References 
    - Information-oriented descriptions of functions and how to operate them
    - Does not include explanations 
2. Explanations
    - Understanding-oriented 
    - Does not include reference to usage
3. How-to guides
    - Goal-oriented 
    - Guides the user on how to solve something specific
4. Tutorials
    - Learning-oriented
    - Serves the user's acquisition of skills and knowledge (not solving a specific problem)

## Terminology

Key words "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", and "MAY" are used per [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Linting
Use the [Ruff linter](https://docs.astral.sh/ruff/linter/) with "google" convention for docstring style. 

## Style
Follow [Google's styleguide](https://google.github.io/styleguide/pyguide.html) for specifics on how to format.

## Documentation folder structure
In `docs/`: All stand-alone documentation (references) as well as explanations, design choices, standards, etc. Anything that cannot or SHOULD NOT be documented in the code itself.
In `examples/`: Long-form examples, tutorials, and how-to guides. 

## References
References SHOULD primarily be written in docstrings. 

### Type annotations
Functions MUST be type annotated.

### Docstrings

#### Modules
Every module SHOULD start with a docstring describing the contents and usage of the module. One MAY include _explanation_ in this docstring as well. This is NOT REQUIRED for test modules.

#### Functions
Every function or class MAY have a docstring. Every function or class that has one or more of the following properties MUST have a docstring:

* Public API
* Non-trivial size
* Non-obvious or complex logic

Docstrings SHOULD follow [Google's styleguide](https://google.github.io/styleguide/pyguide.html). 

#### Examples
All public functions MUST have an example in their docstring. The example MAY be self-contained, but the intention of the example is to showcase how to use the function. 
Internal functions SHOULD have an example in their docstring.

Examples SHOULD be runnable with `doctest`. Hardware-dependent examples SHOULD use CPU fallback when possible. If no CPU fallback exists, examples MAY be illustrative only. Read more on `doctest` [here](https://docs.python.org/3/library/doctest.html). 

Read more on references [here](../diataxis/references.md). For FFI-specific guidance, see [ffi.md](ffi.md).

## Explanations
You MUST NOT include explanations in references (docstrings). Explanations MAY be written in inline comments as well. 

### Inline comments
Inline comments SHOULD replace the need for explaining something at a code review. See inline comments as explanations of complex operations or non-obvious lines of code. Inline comments MUST NOT replace docstrings. Use `TODO` comments for code that is temporary, a short-term solution, or good-enough but not perfect.

### Long-form explanations
Long-form explanations SHOULD be placed in the `docs/` folder. Explanations could for example include mathemical derivations or explanations of complex procedures. For example "How the kernel smoothing procedure works". Explanations are written for humans to increase insight into a subject.

Read more on explanations [here](../diataxis/explanations.md).

## How-to guides 
How-to guides and long-form examples SHOULD be placed in `examples/`. How-to guides SHOULD focus on solving a concrete goal, for example "How to cut a mesh with `cai-geometry`". The purpose of such a guide is to help the already-competent user (in your library) perform a particular task correctly.

How-to guides MAY be written as Jupyter notebooks, scripts, or something third. Usually, a notebook will be the best choice.

Read more on how-to guides [here](../diataxis/how-to-guides.md).

## Tutorials
A tutorial's purpose is to help the user acquire competence. In contrast to how-to guides, tutorials do not assume familiarity with the package. All libraries SHOULD contain a `Getting Started` tutorial, which SHOULD be placed in the `README`. The tutorial MUST be _explicit about the basics_. 

If you are about to write a tutorial, ask yourself: _Am I really about to write a how-to guide?_ 

Read more on tutorials [here](../diataxis/tutorials.md).

## Deprecation

When deprecating functions:

1. Use `warnings.warn()` with `DeprecationWarning` in the function body
2. Start the docstring summary with "Deprecated:"
3. Include the version deprecated and the alternative function

**Example:**
```python
def old_function():
    """Deprecated: Use new_function instead.
    
    Deprecated since v1.2.0. Will be removed in v2.0.0.
    """
    warnings.warn(
        "old_function is deprecated, use new_function",
        DeprecationWarning,
        stacklevel=2
    )
```

## Versioning Documentation

When maintaining documentation across multiple package versions:

1. Documentation lives with code in the same branch/tag
2. Mark version-specific behavior explicitly: "Added in v1.2.0" or "Changed in v2.0.0"
3. Keep a CHANGELOG.md following [Keep a Changelog](https://keepachangelog.com/) format

## AI Guidance

AI assistants writing documentation MUST default to [Google's styleguide](https://google.github.io/styleguide/pyguide.html) for docstrings. AI MUST follow conventions in the `documentation/` folder when they exist, as these take precedence over general style guides. AI SHOULD check `cai-practices` before writing documentation to ensure consistency.

