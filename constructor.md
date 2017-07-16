# DeepStorage constructor

Creates a new DeepStorage instance with initial state:

```
const storage = new DeepStorage({ timer: 0 });
```

While DeepStorage can contain any types as leaf nodes, internal nodes must be arrays or regular JavaScript 'objects' to support partitioning.

