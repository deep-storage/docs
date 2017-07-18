# DeepAsync run

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
asyncIpJson.run();
```



