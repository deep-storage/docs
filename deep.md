# DeepStorage deep

Returns a new DeepStorage instance that only operates against a part of the state tree. 

```
const storage = new DeepStorage({
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
