# DeepStorage addSubscriber

addSubscriber_: \(subscriber: Subscriber\) =&gt; void;_

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

const subscriber = new Subscriber();

subscriber.onChange((path, newState, oldState) => {
    console.log('change!');
});

storage.deep('companies').deep('d24d59de').addSubscriber(subscriber);
storage.deep('companies').deep('d24d59de').deep('name').set('Google');

// outputs: change!

storage.deep('companies').deep('d24d59de').removeSubscriber(subscriber);
```

Use addSubscriber to subscribe to change events in deep storage. Use removeSubscriber to stop listening to change events.

