# DeepStorage state

Returns the part of the state tree under a path

```
const storage = deepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

console.log(storage.stateIn('companies', 'd24d59de', name)); // logs: 'Github'
```



