# DeepAsync constructor

_deepAsync = \(process: \(request\) =&gt; Promise\): DeepAsync_

Create a new deepAsync using the deepAsync default method from 'deep-storage'.

```
import { deepAsync } from 'deep-storage';

const asyncIpJson = deepAsync(
    async () => {
        const response = await fetch.get('http://ip-api.com/json');
        return await response.json();
    }
);

console.log(asyncIpJson.completed); // false
console.log(asyncIpJson.data);      // undefined

await asyncIpJson.run();

console.log(asyncIpJson.completed); // true
console.log(asyncIpJson.data);      // response of http://ip-api.com/json
```



