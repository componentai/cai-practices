# FFI Documentation

Guidelines for documenting Python functions that use Foreign Function Interface (FFI) bindings to other languages (Futhark, Rust, CUDA, etc.).

## Principles

FFI functions have unique documentation needs because they bridge Python with lower-level implementations. 

## FFI Backend References

Docstrings MUST mention the FFI backend.

**Examples of backend references:**
- "Dispatches to Futhark."
- "Calls Rust implementation via PyO3."
- "Executes CUDA kernel."

The backend reference SHOULD appear in the docstring summary.

## Type Mappings

Document type conversions in each function's `Args:` section. Users need to know how Python types map to the FFI language types.

**Format:**
```
Args:
    param_name: Description. Converted to [FFI type].
```

**Examples:**
```python
Args:
    data: Input array. Converted to Futhark f32 array.
    indices: Index array. Converted to Rust Vec<usize>.
    matrix: 2D array. Converted to CUDA device memory (float32).
```

## Error Handling

All FFI errors MUST be wrapped in Python exceptions. Document only the Python exception in the `Raises:` section.

- DO wrap low-level errors in appropriate Python exceptions (`ValueError`, `RuntimeError`, `TypeError`, etc.)
- DO NOT expose raw FFI error types or messages in public API documentation
- DO provide meaningful error messages that help Python users debug issues

## Example Docstring

```python
def compute_kernel(data: np.ndarray) -> np.ndarray:
    """Compute X using optimized Futhark kernel.
    
    Args:
        data: Input array. Converted to Futhark f32 array.
    
    Returns:
        Result array as np.float32.
    
    Raises:
        ValueError: If data has invalid shape.
    
    Example:
        >>> result = compute_kernel(np.array([1.0, 2.0]))
    """
```
