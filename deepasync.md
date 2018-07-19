# DeepAsync

DeepAsync is a wrapper around a deep storage that keeps track of the state of an asynchronous call

```
import { deepAsync } from 'deep-storage';

const asyncIpJson = deepAsync(
    async () => {
        const response = await fetch.get('http://ip-api.com/json');
        return await response.json();
    }
);


```



