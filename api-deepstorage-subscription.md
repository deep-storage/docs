# DeepStorage subscription

_subscription: \(callback: \(path, newState, oldState\) =&gt; void\) =&gt; DeepSubscription;_

Creates a new subscription.

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

Multiple paths can be subscribed to in a single subscription using the subscribeTo method. A subscription is cancelled using the cancel method.

