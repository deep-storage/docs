# DeepAsync constructor

_deepAsync = \(process: \(request\) =&gt; Promise\): Promise_

Create a new deepAsync using the deepAsync default method from 'deep-storage/async'.

```
import { deepAsync } from 'deep-storage';

const asyncIpJson = await deepAsync(
    async () => {
        const response = await fetch.get('http://ip-api.com/json');
        return await response.json();
    }
);
```



