# DeepStorage setIn

_setIn: \(...path\) =&gt; \(newValue\) =&gt; Promise;_

Sets a value in the state tree e.g.

```
const storage = deepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

// set company 'd24d59de''s name to 'Google'
await storage.setIn('companies', 'd24d59de', 'name')('Google');
```

setIn is essentially a shortcut for an updateIn where the old value is ignored. setIn will trigger callbacks to subscribers interested in the part of the state tree that's being updated.

If a path does not exist, deep storage will create the intermediate nodes as objects e.g.

```
const storage = deepStorage({
});

// set company 'd24d59de''s name to 'Google'
await storage.setIn('companies', 'd24d59de', 'name')('Google');

console.log(storage.state);

// { companies: { d24d59de: { name: 'Google' } }
```

This is similar to how [immutablejs's setIn](https://facebook.github.io/immutable-js/docs/#/Map/setIn) behaves

