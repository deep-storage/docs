# DeepAsync constructor

_deepAsync = \(storage, process: \(request\) =&gt; Promise\)_

Create a new deepAsync using the deepAsync default method from 'deep-storage/async'.

```
import deepStorage from 'deep-storage';
import deepAsync from 'deep-storage/async';

const storage = deepStorage({});
const asyncIpJson = deepAsync(
    storage.deep('ipJson'),
    async () => {
        const response = await fetch.get('http://ip-api.com/json');
        return await response.json();
    }
);
```


