# DeepStorage constructor

_deepStorage\(initialState\): DeepStorage_

Creates a new DeepStorage instance with initial state:

```
import { deepStorage } from 'deep-storage';

const storage = deepStorage({ timer: 0 });
```

While DeepStorage can contain any types as leaf nodes, internal nodes must be regular JavaScript 'objects' to support partitioning.

