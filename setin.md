# DeepStorage setIn

Sets a value in the state tree e.g.

```
const storage = new DeepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

// set company 'd24d59de''s name to 'Google'
storage.setIn('companies', 'd24d59de', 'name')('Google');
```

setIn is essentially a shortcut for an updateIn where the old value is ignored. setIn will trigger callbacks to subscribers interested in the part of the state tree that's being updated.

