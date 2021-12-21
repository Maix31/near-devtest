Example of NEAR Wallet integration
==================================

This example demonstrates how to integrate your application with NEAR Wallet.
The contract is quite simple. It can store the account_id of last sender and return it. 
It also shows how you can debug contracts using logs.

## Getting started

The config of the repo is already preset to connect to the devtest.testnet Contract
You will only have to research the near-sdk-js and write the code that connects to it
and calls both of its methods "sayHi" and "whoSaidHi"
and complete the functionality of the page so it is functional, by populating the variables in the src/components/Tutorial.vue

### Quickest option

1. Install dependencies:

```
yarn
```

2. Start the development server to see further instructions:

```
yarn dev
```

Your command line which will display a link to localhost similar to:
```bash
Listening on: http://localhost:3000/
```

Please open that link your browser to continue and see how to log in with NEAR Wallet in a simple webapp.
