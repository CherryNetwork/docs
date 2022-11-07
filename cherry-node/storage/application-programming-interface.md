# Application Programming Interface

### Cherry Node IPFS Features

#### Ownerships

Share your files with other peers through _**OwnershipLayers (Owner, Editor, Reader)**_. You can give and/or revoke the _OwnershipLayer_ of any peer as long as your are the Owner of the IPFS asset.

{% hint style="info" %}
* Owners can read, edit and delete an IPFS asset.
* Editors can read and edit an IPFS asset.
* Readers can only read an IPFS asset.
{% endhint %}

Change the OwnershipLayer you have given to any peer, as long as you are the Owner of the asset.

Pin any IPFS asset that someone shared with you.

{% hint style="info" %}
Files you upload are automatically pinned.\
\
Pinning an IPFS asset allows you to tell the IPFS to always keep the pinned asset in your local node. Also, by pinning an IPFS asset, you are able to share it with other peers.
{% endhint %}

Unpin any IPFS asset that you do not want to share anymore.

### Callable functions in Cherry

1. `create_ipfs_asset` : Create the file you want to upload.
2. `pin_ipfs_asset` : Pin

#### pin\_ipfs\_asset(origin, address, cid)

Pins an IPFS asset.

{% hint style="info" %}
The IPFS assets you upload, are automatically pinned on creation.
{% endhint %}

{% hint style="warning" %}
You need to be the asset's owner to pin it.
{% endhint %}

#### unpin\_ipfs\_asset(origin, address, cid)

Unpins an IPFS asset you own.

{% hint style="warning" %}
You need to be the asset's owner to unpin it.
{% endhint %}

#### delete\_ipfs\_asset(origin, address, cid)

Inserts the file you want to delete in a data queue. The actual IPFS deletion is done in the `submit_ipfs_delete_results` function.

{% hint style="warning" %}
You need to be the asset's owner to delete it.\
Only unpinned assets can be deleted.
{% endhint %}

#### read\_file(origin, address, cid)

Reads an IPFS asset.

{% hint style="warning" %}
You need to have an OwnershipLayer to read a file.
{% endhint %}

#### submit\_ipfs\_identity(origin, public\_key, multiaddress)



#### submit\_ipfs\_add\_results(origin, admin, cid)

Creates and pins an IPFS asset.

#### submit\_ipfs\_pin\_results( )

Returns Ok if the IPFS asset was pinned successfully.

#### submit\_ipfs\_unpin\_results( )

Returns Ok if the IPFS asset was unpinned successfully.

#### submit\_ipfs\_delete\_results(origin, admin, cid)

Deletes an unpinned IPFS asset that you own.

#### add\_owner(origin, cid, add\_acct, ownership\_layer)

Gives an ownership layer to another user.

{% hint style="info" %}
You need to be the owner of the asset to give ownership layers to other users.
{% endhint %}

#### remove\_owner(origin, cid, remove\_acct)

Removes the ownership layer from a user.

{% hint style="info" %}
You need to be the owner of the asset to give ownership layers to other users.
{% endhint %}

#### change\_ownership(origin, cid, acct\_to\_change, ownership\_layer)

Changes the ownership layer of a user.

{% hint style="info" %}
You need to be the owner of the asset to give ownership layers to other users.
{% endhint %}

