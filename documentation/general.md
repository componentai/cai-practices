# Documentation style guide

This style guide for documentation is primarily written for Python, but principles apply to all languages written, if possible.
In this document, "function" means a function, method, generator, or property.

## Principles

We will try to follow [Diàtaxis](https://diataxis.fr/) principles and devide documentation up in four distinct parts:

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

Read more on references [here](todo).

## Explanations
You MUST NOT include explanations in references (docstrings). Explanations MAY be written in inline comments as well. 

### Inline comments
Inline comments SHOULD replace the need for explaining something at a code review. See inline comments as explanations of complex operations or non-obvious lines of code. Inline comments MUST NOT replace docstrings. Use `TODO` comments for code that is temporary, a short-term solution, or good-enough but not perfect.

### Long-form explanations
Long-form explanations SHOULD be placed in the `docs/` folder. Explanations could for example include mathemical derivations or explanations of complex procedures. For example "How the kernel smoothing procedure works". Explanations are written for humans to increase insight into a subject.

Read more on explanations [here](todo).

## How-to guides 
How-to guides and long-form examples SHOULD be placed in `examples/`. How-to guides SHOULD focues on solving a concrete goal, for example "How to cut a mesh with `cai-geometry`". The purpose of such a guide is to help the already-competent user (in your library) perform a particular task correctly.

Read more on how-to guides [here](todo).

## Tutorials
A tutorial's purpose is to help the user acquire competance. In contrast to how-to guides, tutorials do not assume familiarity with the package. All libraries SHOULD contain a `Getting Started` tutorial, which SHOULD be placed in the `README`. The tutorial MUST be _explicit about the basics_. 

Read more on tutorials [here](todo).
