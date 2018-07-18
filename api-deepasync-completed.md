# DeepAsync completed

Whether the deep async has completed. True if has succeeded for failed otherwise false.

    import { deepAsync } from 'deep-storage';

    const asyncIpJson = await deepAsync(
        async (ip) => {
            const response = await fetch.get(`http://ip-api.com/json/${ip}`);
            return await response.json();
        }
    );

    console.log(asyncIpJson.completed); // false

    asyncIpJson.run('8.8.8.8').then(() => {
        console.log(asyncIpJson.completed) // true
    })



