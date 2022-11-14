# Application Programming Interface

### Cherry Node IPFS Features

#### Ownerships

Share your files with other accounts through _**OwnershipLayers (Owner, Editor, Reader)**_. You can give and/or revoke the _OwnershipLayer_ of any account as long as your are the Owner of the IPFS asset.

{% hint style="info" %}
* Owners can read, edit, pin, unpin and delete an IPFS asset.
* Editors can read and edit an IPFS asset.
* Readers can only read an IPFS asset.
{% endhint %}

{% hint style="info" %}
Files you upload are automatically pinned.\
\
Pinning an IPFS asset allows you to tell the IPFS to always keep the pinned asset in your local node. Also, by pinning an IPFS asset, you are able to share it with other peers.
{% endhint %}

Unpin any IPFS asset that you do not want to share anymore.

### Callable functions in Cherry

1. `create_ipfs_asset` : Create the file you want to upload.
2. `pin_ipfs_asset` : Pin
3. `unpin_ipfs_asset`: Unpins an IPFS Asset and make it available for garbage collection
4. `delete_ipfs_asset`: Deletes the IPFS Asset from the storage
5. `add_owner`: Add an Owner(Owner, Editor, Reader) to the given IPFS Asset
6. `remove_ownership`: Removes any kind of ownership of the given Account from the given IPFS Asset
7. `change_ownership`: Change the ownership of a given Account of then given IPFS Asset
