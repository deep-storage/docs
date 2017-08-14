# DeepStorage updateIn

_updateIn: \(...path\) =&gt; \(callback\) =&gt; Promise;_

Updates a value in the state tree e.g.

```
const storage = deepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

// set company 'd24d59de''s name to 'github'
await storage.updateIn('companies', 'd24d59de', 'name')(prev => prev.toLowerCase());
```

updateIn will trigger callbacks to subscribers interested in the part of the state tree that's being updated. The updateIn callback should not mutate the previous value.

If a path does not exist, deep storage will create the intermediate nodes as objects e.g.

```
const storage = deepStorage({
});

// set company 'd24d59de''s name to 'Google'
await storage.setIn('companies', 'd24d59de')(prevState => { name: 'Google' });

console.log(storage.state);

// { companies: { d24d59de: { name: 'Google' } }
```

This is similar to how [immutablejs's updateIn](https://facebook.github.io/immutable-js/docs/#/Map/updateIn) behaves

