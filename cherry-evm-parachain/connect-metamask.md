# How to connect your MetaMask wallet to Cherry EVM

This tutorial will guide you through the process of connecting your MetaMask wallet to Cherry EVM.

If you do not already have MetaMask installed, you can install the extension from the [Chrome Store](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en). Follow the [Getting Started with MetaMask](https://support.metamask.io/hc/en-us/articles/360015489531-Getting-Started-With-MetaMask) guide from the official MetaMask documentation. Once you have the MetaMask extension, follow the account creation wizard. Make sure to store your mnemonic safely and do not share it with anyone.

## Connect to Cherry EVM

Navigate to the **Add Network** section of MetaMask. You can find it at the bottom of the list of available networks, after clicking on the currently active network.

![Add network](<../.gitbook/assets/addNetwork.png>)

From there, click the **Add a network manually** button, located at the bottom of the popular custom networks.

![Add custom network](<../.gitbook/assets/addCustomNetwork.png>)

This should open up a form to add a new network to your MetaMask (you might have to unlock MetaMask before it opens). Once the form is opened, use the following information to add the Cherry EVM network.

### Cherry EVM parachain details

**Network name**: Cherry EVM Testnet  
**New RPC URL**:   
**Chain ID**: 254  
**Currency symbol**: TPCHER  

Leave the **Block Explorer URL** empty for now.

![Custom network information](<../.gitbook/assets/customNetworkInfo.png>)

Cherry EVM should now be connected and you should see your TPCHER balance (if you have any).

![MetaMask balance](<../.gitbook/assets/metamaskBalance.png>)

You might have to bind your MetaMask account to your Substrate account in order to see your balance. Documentation on how to do it is available [here](link to another page).