# DeepStorage state

_stateIn: \(...path\) =&gt; DeepState;_

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

If a path does not exist, deep storage will create the intermediate nodes as objects and return undefined

