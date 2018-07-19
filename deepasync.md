# DeepAsync

DeepAsync is a wrapper around a deep storage that keeps track of the state of an asynchronous call

```
import { deepAsync } from 'deep-storage';

const asyncIpJson = await deepAsync(
    async () => {
        const response = await fetch.get('http://ip-api.com/json');
        return await response.json();
    }
);

console.log(asyncIpJson.completed); // false
console.log(asyncIpJson.data);      // undefined

await asyncIpJson.run();            // goes through created, running, completed

console.log(asyncIpJson.completed); // true
console.log(asyncIpJson.data);      // response of http://ip-api.com/json (assuming it succeeded)
```



