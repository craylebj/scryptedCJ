# Use the Scrypted SDK from the command line or web

```js
import { connectScryptedClient, OnOff } from '@scrypted/client';

async function example() {
    const sdk = await connectScryptedClient({
        baseUrl: 'https://localhost:10444',
        pluginId: "@scrypted/core",
        username: process.env.SCRYPTED_USERNAME || 'admin',
        password: process.env.SCRYPTED_PASSWORD || 'swordfish',
    });

    const dimmer = sdk.systemManager.getDeviceByName<OnOff>("Office Dimmer");
    dimmer.turnOn();
    await new Promise(resolve => setTimeout(resolve, 5000));
    await dimmer.turnOff(); 
    // allow node to exit
    sdk.disconnect();
}

example();
```

# Running the Example

```sh
npm -g install ts-node
ts-node examples/example.ts
```
