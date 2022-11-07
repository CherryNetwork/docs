# Create an Account

An address is the public part of a Cherry account. The private part is the key used to access this address. The public and private part together make up a Cherry account. To interact with Cherry  chain create such as creating basic transactions and various operation, you need to have a created Account.

There are several ways to generate a Cherry account:

* [​Polkadot{.js} Browser Plugin ](https://polkadot.js.org/extension/)- _We recommend this for most users_
* ​[Subkey](https://docs.edgeware.wiki/quickstart/create-an-account#subkey) - _Advanced and Most secure_
* ​[Cherry.Place​](http://cherry.place)
* Parity Signer
* Ledger Hardware Wallet

## Storing your key safely <a href="#storing-your-key-safely" id="storing-your-key-safely"></a>

The seed is your **key** to the account. Knowing the seed allows you, or anyone else who knows the seed, to re-generate and control this account.&#x20;

It is imperative to store the seed somewhere safe, secret, and secure. If you lose access to your account (i.e. you forget the password for your account's JSON file), you can re-create it by entering the seed. This also means that somebody else can have control over your account if they have access to your seed.

For maximum security, the seed should be written down on paper or another non-digital device and stored in a safe place. You may also want to protect your seed from physical damage, as well (e.g. by storing in a sealed plastic bag to prevent water damage, storing it in a fireproof safe, etching it in metal, etc.) It is recommended that you store multiple copies of the seed in geographically separate locations (e.g., one in your home safe and one in a safety deposit box at your bank).You should definitely not store your seed on any kind of computer that has or may have access to the internet in the future.

## Storing your account's JSON file <a href="#storing-your-accounts-json-file" id="storing-your-accounts-json-file"></a>

The JSON file is encrypted with a password, which means you can import it into any wallet which supports JSON imports, but to then use it, you need the password. You don't have to be as careful with your JSON file's storage as you would with your seed (i.e. it can be on a USB drive near you), but remember that in this case your account is only as secure as the password you used to encrypt it. Do not use easy to guess or hard to remember passwords. It is good practice to use a [mnemonic password of four to five words](https://xkcd.com/936/). These are nearly impossible for computers to guess due to the number of combinations possible, but much easier for humans to remember.

## Polkadot{.js} Browser Plugin <a href="#polkadot-.js-browser-plugin" id="polkadot-.js-browser-plugin"></a>

The Polkadot{.js} plugin provides a reasonable balance of security and usability. It provides a separate local mechanism to generate your address and interact with Polkadot.This method involves installing the Polkadot{.js} plugin and using it as a “virtual vault," separate from your browser, to store your private keys. It also allows signing of transactions and similar functionality.

It is still running on the same computer you use to connected to the internet with and thus is less secure than using Parity Signer or other air-gapped approaches.

## Install the Browser Plugin <a href="#install-the-browser-plugin" id="install-the-browser-plugin"></a>

The browser plugin is available for [both Google Chrome (and Chromium based browsers like Brave) and FireFox.](https://polkadot.js.org/extension/)​If you would like to know more or review the code of the plugin yourself, [you can visit the Github source repository](https://github.com/polkadot-js/extension).

After installing the plugin, you should see the orange and white Polkadot{.js} logo in the menu bar of your browser.

Install Polkadot Chrome Extension

![](https://docs.edgeware.wiki/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MWyXA0bgrUw7ynlH\_ge%2Fuploads%2Fgit-blob-906584861d48176d3e053de8042ebc219e800fbd%2Finstall\_polkadot\_chrome\_extension.png?alt=media)

## Open Accounts <a href="#open-accounts" id="open-accounts"></a>

Navigate to [Cherry.Place](http://cherry.place). Click on the "Accounts" tab.

## Create Account <a href="#create-account" id="create-account"></a>

Open the Polkadot{.js} browser extension by clicking the logo on the top bar of your browser. You will see a browser popup not unlike the one below.

![Create an account in the polkadot extension](https://docs.edgeware.wiki/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MWyXA0bgrUw7ynlH\_ge%2Fuploads%2Fgit-blob-96d0e01177b07c6bc581f0d97a350797ad0790cb%2Fimport\_account\_to\_extension.png?alt=media)

Click the big plus button or select "Create new account" from the small plus icon in the top right. The Polkadot{.js} plugin will then use system randomness to make a new seed for you and display it to you in the form of twelve words.

![mnemonic seed for your new account](https://docs.edgeware.wiki/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MWyXA0bgrUw7ynlH\_ge%2Fuploads%2Fgit-blob-fde4b40a194162a01de27bf8a41afe7d8952f24b%2Fmnemonic\_seed\_for\_new\_account.png?alt=media)

You should back up these words as explained above. It is imperative to store the seed somewhere safe, secret, and secure. If you cannot access your account via Polkadot{.js} for some reason, you can re-enter your seed through the "Add account menu" by selecting "Import account from pre-existing seed".

![import account to extension](https://docs.edgeware.wiki/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MWyXA0bgrUw7ynlH\_ge%2Fuploads%2Fgit-blob-3dfe59dd0ee18f07686d139d13e913f48e6b3998%2Fcreate\_account\_in\_extension.png?alt=media)

## Name Account <a href="#name-account" id="name-account"></a>

The account name is arbitrary and for your use only. It is not stored on the blockchain and will not be visible to other users who look at your address via a block explorer. If you're juggling multiple accounts, it helps to make this as descriptive and detailed as needed.

## Enter Password <a href="#enter-password" id="enter-password"></a>

The password will be used to encrypt this account's information. You will need to re-enter it when using the account for any kind of outgoing transaction or when using it to cryptographically sign a message. Note that this password does NOT protect your seed phrase. If someone knows the twelve words in your mnemonic seed, they still have control over your account even if they do not know the password.

## Set Address for Cherry Mainnet <a href="#set-address-for-edgeware-mainnet" id="set-address-for-edgeware-mainnet"></a>

Now we will ensure that the addresses are displayed as Cherry mainnet addresses.

Click on "Options" at the top of the plugin window, and under "Display address format for" select "Cherry".

![Set Address for Cherry Mainnet](https://docs.edgeware.wiki/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MWyXA0bgrUw7ynlH\_ge%2Fuploads%2Fgit-blob-6e98c261e6ca6747e0004f24829ffa77e4fb8f51%2Fset\_address\_for\_edgeware\_mainnet.png?alt=media)

Your address' format is only visual - the data used to derive this representation of your address are the same, so you can use the same address on multiple chains. However, for privacy reasons, we recommend creating a new address for each chain you're using.

## Subkey <a href="#subkey" id="subkey"></a>

Subkey is recommended for technically advanced users who are comfortable with the command line and compiling Rust code. Subkey allows you to generate keys on any device that can compile the code. Subkey may also be useful for automated account generation using an air-gapped device. It is not recommended for general users.

​[You can find detailed build and usage instructions of subkey](https://github.com/paritytech/substrate/tree/master/bin/utils/subkey)​

![Subkey generate address for Cherry](https://docs.edgeware.wiki/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MWyXA0bgrUw7ynlH\_ge%2Fuploads%2Fgit-blob-4d1d86f22cd7ef711e4f2b866fe40d44e3f299cb%2Fsubkey\_generate\_address\_for\_edgeware.png?alt=media)

## Cherry.Place <a href="#edgeui-flax.vercel.app" id="edgeui-flax.vercel.app"></a>

> Please note! If you use this method to create your account and clear your cookies in your browser, your account will be lost forever if you do not back it up. Make sure you store your seed phrase in a safe place, or download the account's JSON file if using the Polkadot{.js} browser extension. Learn more about account backup and restoration here.

**Using the Cherry.Place user interface without the plugin is not recommended.** It is the least secure way of generating an account. It should only be used if all of the other methods are not feasible in your situation.

## Open Cherry.Place <a href="#open-edgeui-flax.vercel.app" id="open-edgeui-flax.vercel.app"></a>

Navigate to [cherry.place](http://cherry.place) and click on "Accounts" underneath the Accounts tab. It is located in the navigation bar at the top of your screen.

![](https://user-images.githubusercontent.com/44712760/123108135-646a4100-d3f7-11eb-9ec0-c0ba2659964c.png)

## Start Account Generation <a href="#start-account-generation" id="start-account-generation"></a>

Click on the "Add Account" button. You should see a pop-up similar to the process encountered when using the [Polkadot JS Extension method](https://docs.edgeware.wiki/quickstart/create-an-account#polkadotjs-browser-plugin) above. Follow the same instructions and remember to [store your seed safely](https://docs.edgeware.wiki/quickstart/create-an-account#storing-your-key-safely)!

## Create and Back Up Account <a href="#create-and-back-up-account" id="create-and-back-up-account"></a>

Click “Save” and your account will be created. It will also generate a backup JSON file that you should safely store, ideally on a USB off the computer you're using. You should not store it in cloud storage, email it to yourself, etc.

You can use this backup file to restore your account. This backup file is not readable unless it is decrypted with the password.

## Reference <a href="#reference" id="reference"></a>

* ​[Account generation for Polkadot Relay chain](https://wiki.polkadot.network/docs/en/learn-account-generation)​
* ​[SS58 Adress Transform](https://polkadot.subscan.io/tools/ss58\_transform)​
