# DeepStorage deep

_deep: \(...path\) =&gt; DeepStorage;_

Returns a new DeepStorage instance that only operates against a part of the state tree.

```
const storage = deepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

const companiesStorage = storage.deep('companies'));
```

Note: changes to the state will propagate up to subscribers in the parent state.

