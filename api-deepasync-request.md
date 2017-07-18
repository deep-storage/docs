# DeepAsync request

    import deepStorage from 'deep-storage';
    import deepAsync from 'deep-storage/async';

    const storage = deepStorage({});
    const asyncIpJson = deepAsync(
        storage.deep('ipJson'),
        async (ip) => {
            const response = await fetch.get(`http://ip-api.com/json/${ip}`);
            return await response.json();
        }
    );
    asyncIpJson.run('8.8.8.8');

    console.log(asyncIpJson.request) // 8.8.8.8



