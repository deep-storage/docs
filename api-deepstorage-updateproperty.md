# DeepStorage updateProperty

_updateProperty: \(key, callback\) =&gt; Promise;_

Updates a value one level down in the state tree

```
const storage = deepStorage({
    count: 1
});

await storage.updateProperty('count', prev => prev + 1);
```

updateProperty will trigger callbacks to subscribers interested in the part of the state tree that's being updated. The updateProperty callback should not mutate the previous value.

