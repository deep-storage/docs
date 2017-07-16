# DeepStorage updateIn

Updates a value in the state tree e.g.

```
const storage = new DeepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

// set company 'd24d59de''s name to 'github'
storage.updateIn('companies', 'd24d59de', 'name')(prev => prev.toLowerCase());
```

updateIn will trigger callbacks to subscribers interested in the part of the state tree that's being updated. The updateIn callback should not mutate the previous value.

