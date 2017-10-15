# DeepAsync completed

Whether the deep async has completed. True if has succeeded for failed otherwise false.

    import deepStorage from 'deep-storage';
    import deepAsync from 'deep-storage/async';

    const storage = deepStorage({});
    const asyncIpJson = await deepAsync(
        storage.deep('ipJson'),
        async (ip) => {
            const response = await fetch.get(`http://ip-api.com/json/${ip}`);
            return await response.json();
        }
    );

    console.log(asyncIpJson.completed); // false

    asyncIpJson.run('8.8.8.8').then(() => {
        console.log(asyncIpJson.completed) // true
    })



