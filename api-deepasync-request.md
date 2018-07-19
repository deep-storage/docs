# DeepAsync request

    import { deepAsync } from 'deep-storage';

    const asyncIpJson = deepAsync(
        async (ip) => {
            const response = await fetch.get(`http://ip-api.com/json/${ip}`);
            return await response.json();
        }
    );
    asyncIpJson.run('8.8.8.8');

    console.log(asyncIpJson.request) // 8.8.8.8



