# Subscription subscribeTo

_subscribeTo: \(...path\) =&gt; void;_

Subscribes to a path

```
const storage = deepStorage({
    companies: {
        'd24d59de': {
            id: 'd24d59de'
            name: 'Github'
        }
    }
});

const subscription = storage.subscription((path, newState, oldState) => {
    console.log('change!');
});

subscription.subscribeTo('companies', 'd24d59de');

storage.setIn('companies', 'd24d59de', 'name')('Google');

// outputs: change!

subscription.cancel();
```



