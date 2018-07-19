# DeepAsync run

```
import { deepAsync } from 'deep-storage';

const asyncIpJson = deepAsync(
    async () => {
        const response = await fetch.get('http://ip-api.com/json');
        return await response.json();
    }
);
await asyncIpJson.run();
```



