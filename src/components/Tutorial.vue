<!-- Please remove this file from your project -->
<template>
  <div class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center py-8">
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css" rel="stylesheet">
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <a class="flex justify-center pt-8 sm:pt-0 h-32" href="https://docs.near.org/docs/api/naj-quick-reference" target="_blank">
        <NEARLogo></NEARLogo>
      </a>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-2xl leading-7 font-semibold">
          Welcome to your NEAR Javascript SDK Test
        </h2>
        <p class="mt-3 text-gray-600">
          We recommend you take a look at the
					<a href="https://docs.near.org/docs/api/naj-quick-reference" target="_blank"
						class="button--doc text-purple-500 hover:underline">near-api-js documentation</a>,
					whether you are new or have previous experience with the framework.<br>
        </p>
        <p class="mt-4 pt-4 text-gray-800 border-t border-dashed">
          Use the NEAR SDK to connect to the NEAR testnet, to do so you will need to create a
					<a href="https://wallet.testnet.near.org/create" target="_blank"
						class="button--doc text-purple-500 hover:underline">Testnet Account</a>
        </p>
        <p class="mt-4 pt-4 text-gray-800 border-t border-dashed">
          Then use this button to record send a request to our devtest.testnet contract using its 'sayHi' method.
        </p>

				<button class="bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded-full mt-6 mx-auto w-32 block"
								@click="sayHi">
					Say Hi!
				</button>
				<p class="mt-4 pt-4 text-gray-800 border-t border-dashed italic">
					If you want to have a look at the Contract Code that is running on devtest.testnet,
					have a look at
					<code class="bg-gray-100 text-sm p-1 rounded border">assembly/index.ts</code>
				</p>
        <p class="mt-4 pt-4 text-gray-800 border-t border-dashed">
          Then read the data from the blockchain using the contract's 'whoSaidHi' method and display it here
        </p>
				<h1 class="mt-4 text-lg text-center shadow-sm border-solid border-2 border-light-grey-100">
					<a id="who" :class="{'no-underline hover:underline cursor-pointer text-purple-600': link_to_who_said_hi_account}" target="_blank"
						 @click="openURLNewTab(link_to_who_said_hi_account)">{{ who_said_hi_account !== 'No one' ? who_said_hi_account : "Who" }}</a>
					was the last person to 'sayHi' {{ who_said_hi_account !== 'No one' ? '!' : '?'}}
				</h1>
        <p class="mt-4 pt-4 text-gray-800 border-t border-dashed">
          To get started, go to <code class="bg-gray-100 text-sm p-1 rounded border">src/components/Tutorial.vue</code> and start coding. Have fun!
        </p>
				<footer class="mt-16">
					<p v-if="walletAccount && walletAccount.isSignedIn()" class="">
						Signed in as
						<a id="account-id" class="signed-in no-underline hover:underline cursor-pointer text-purple-600"
							 href="https://wallet.testnet.near.org/profile" target="_blank">
							{{walletAccount.getAccountId()}}
						</a>
							•
						<a class="no-underline hover:underline cursor-pointer text-purple-600"
							 @click="signOut" id="sign-out">
							Sign Out
						</a>
					</p>
					<p v-else class="signed-out">
						<button class="bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded-full"
										@click="signedOutFlow">
							Sign In with NEAR
						</button>
					</p>
				</footer>
      </div>
      <div class="flex justify-center pt-4 space-x-2">
        <a href="https://github.com/near" target="_blank"><svg
          class="w-6 h-6 text-gray-600 hover:text-gray-800 button--github"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          aria-hidden="true"
          role="img"
          width="32"
          height="32"
          preserveAspectRatio="xMidYMid meet"
          viewBox="0 0 24 24"><path d="M12 2.247a10 10 0 0 0-3.162 19.487c.5.088.687-.212.687-.475c0-.237-.012-1.025-.012-1.862c-2.513.462-3.163-.613-3.363-1.175a3.636 3.636 0 0 0-1.025-1.413c-.35-.187-.85-.65-.013-.662a2.001 2.001 0 0 1 1.538 1.025a2.137 2.137 0 0 0 2.912.825a2.104 2.104 0 0 1 .638-1.338c-2.225-.25-4.55-1.112-4.55-4.937a3.892 3.892 0 0 1 1.025-2.688a3.594 3.594 0 0 1 .1-2.65s.837-.262 2.75 1.025a9.427 9.427 0 0 1 5 0c1.912-1.3 2.75-1.025 2.75-1.025a3.593 3.593 0 0 1 .1 2.65a3.869 3.869 0 0 1 1.025 2.688c0 3.837-2.338 4.687-4.563 4.937a2.368 2.368 0 0 1 .675 1.85c0 1.338-.012 2.413-.012 2.75c0 .263.187.575.687.475A10.005 10.005 0 0 0 12 2.247z" fill="currentColor" /></svg></a>
        <a href="https://twitter.com/NEARProtocol" target="_blank"><svg
          class="w-6 h-6 text-gray-600 hover:text-gray-800"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          aria-hidden="true"
          role="img"
          width="32"
          height="32"
          preserveAspectRatio="xMidYMid meet"
          viewBox="0 0 24 24"><path d="M22.46 6c-.77.35-1.6.58-2.46.69c.88-.53 1.56-1.37 1.88-2.38c-.83.5-1.75.85-2.72 1.05C18.37 4.5 17.26 4 16 4c-2.35 0-4.27 1.92-4.27 4.29c0 .34.04.67.11.98C8.28 9.09 5.11 7.38 3 4.79c-.37.63-.58 1.37-.58 2.15c0 1.49.75 2.81 1.91 3.56c-.71 0-1.37-.2-1.95-.5v.03c0 2.08 1.48 3.82 3.44 4.21a4.22 4.22 0 0 1-1.93.07a4.28 4.28 0 0 0 4 2.98a8.521 8.521 0 0 1-5.33 1.84c-.34 0-.68-.02-1.02-.06C3.44 20.29 5.7 21 8.12 21C16 21 20.33 14.46 20.33 8.79c0-.19 0-.37-.01-.56c.84-.6 1.56-1.36 2.14-2.23z" fill="currentColor" /></svg></a>
      </div>
    </div>
  </div>
</template>

<script>
import * as nearAPI from 'near-api-js'
import getConfig from '../config/config.js'
import NEARLogo from './NEARLogo'
export default {
	name: 'NuxtTutorial',
	components: { NEARLogo },
	data() {
		return {
			config: getConfig('development'),
			near: null,
			walletAccount: null,
			accountId: null,
			contract: null,
			who_said_hi_account: 'No one',
			link_to_who_said_hi_account: null,
		}
	},
	async mounted() {
		console.log('Loaded Config', this.config)
		
		// Add Wallet Init code here

		const config = { 
			...this.config, 
			...{
				// creates keyStore using private key in local storage
				// *** REQUIRES SignIn using walletConnection.requestSignIn() ***
				keyStore: new nearAPI.keyStores.BrowserLocalStorageKeyStore() 
			} 
		};

		// connect to NEAR
		this.near = await nearAPI.connect(config);
		// create wallet connection
		this.walletAccount = new nearAPI.WalletConnection(this.near);
		this.accountId = this.walletAccount.getAccountId();
		this.contract = await this.near.loadContract(
			this.config.contractName, {
				viewMethods: ['whoSaidHi'], // view methods do not change state but usually return a value
    		changeMethods: ['sayHi'], // change methods modify state
    		sender: this.accountId, // account object to initialize and sign transactions.
			}
		);

		this.updateWhoSaidHi();
	},
	methods: {
		signedOutFlow() {
			this.walletAccount.requestSignIn(
				// The contract name that would be authorized to be called by the user's account.
				this.config.contractName,
				// This is the app name. It can be anything.
				'Who was the last person to say "Hi!"?',
				// We can also provide URLs to redirect on success and failure.
				// The current URL is used by default.
			);
		},
		async signedInFlow() {
			this.contract.sayHi().then(updateWhoSaidHi);

			setTimeout(this.updateWhoSaidHi, 1000);
		},
		signOut() {
			this.walletAccount.signOut();
		},
		async updateWhoSaidHi() {
			const who = await this.contract.whoSaidHi();
			console.log(who);
			this.link_to_who_said_hi_account = 'https://explorer.testnet.near.org/accounts/' + who;
			this.who_said_hi_account = who;
		},
		sayHi() {
			if (!this.walletAccount.isSignedIn())
				return this.signedOutFlow();

			this.contract.sayHi()
				.then(() => {
					this.updateWhoSaidHi()
				})
				.catch(console.error)
		},
		openURLNewTab(url) {
			if (url)
				window.open(url, '_blank')
		},
	}
}
</script>
