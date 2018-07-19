# DeepAsync data

    import { deepAsync } from 'deep-storage/async';

    const asyncIpJson = deepAsync(
        async (ip) => {
            const response = await fetch.get(`http://ip-api.com/json/${ip}`);
            return await response.json();
        }
    );

    asyncIpJson.run('8.8.8.8').then(() => {
        console.log(asyncIpJson.data) // {"as":"AS15169 Google Inc.","city":...}
    })



