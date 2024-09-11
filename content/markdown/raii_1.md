Memory is attached to an object. When an object is created, memory is allocated, when the object is destroyed, memory is freed.

- **Memory Leak**: Forget to de-allocate memory.
- **Dangling Pointer**: Accessing memory after de-allocation.

RAII solves memory leak but not dangling pointer.
