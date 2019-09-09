# Compatibility

As the Kiosked script is usually run in a shared environment, potentially alongside other analytics / advertising scripts, some compatibility factors should be considered.

## Existing Google Ads (DFP / GAM)

If you already use Google ad demand on your site, you'll most likely be initiating calls to Google via Google Ad Manager (formerly DFP). As Kiosked scripts also provide Google ad demand, there are a few rare issues that may occur when running both side-by-side.

### GPT refreshing

Google ads can be refreshed using the `googletag.pubads().refresh()` command. This method has far-reaching effects if it is not used properly. Calling this method **without arguments** will refresh all Google units on a page, including any created by Kiosked. While this usually isn't an issue if only your Google ads are running on a page, using this method without arguments makes it difficult or potentially impossible for third parties to use their own monetisation systems if they include Google demand. Refreshing third party ads can have a negative outcome on overall monetisation by way of refreshing _too_ often (if the third party, such as Kiosked, also refresh their ads). Such behaviour can eventually result in the blacklisting of a publisher account, in the worse circumstances.

It is therefore recommended not to make calls to `refresh()` without first providing the **slots** with which to refresh, like so:

```javascript
var slot1 = googletag.defineSlot("/1234/abc-123", [[728, 90]], "ad1"),
    slot2 = googletag.defineSlot("/1234/abc-456", [[728, 90]], "ad2");
// Later:
googletag.pubads().refresh([ slot1, slot2 ]);
```

Being specific with slot references is a great way to ensure that there are no side effects when integrating other ad services.

### Sync Rendering

The GPT API provides a method called [`enableSyncRendering`](https://developers.google.com/doubleclick-gpt/reference#googletag.PubAdsService_enableSyncRendering), which is usually called as follows:

```javascript
googletag.pubads().enableSyncRendering();
```

This method is actually [deprecated by Google](https://developers.google.com/doubleclick-gpt/reference#googletag.PubAdsService_enableSyncRendering):

> [DEPRECATED] Enables sync rendering mode to enable blocking fetching and rendering of ads. This mode must be set before the service is enabled. Synchronous rendering also requires that the GPT JavaScript be loaded synchronously. Synchronous rendering is deprecated and will no longer work after April 16th, 2019. To prepare for this change, we recommend you stop using this API. Asynchronous rendering is the default and provides a faster page load experience.

Not only that, but that particular method (while it's supposed to no longer work) can have strange consequences when used in conjunction with the Kiosked library. Kiosked's script uses _async_ rendering (the new default), which can break when sync rendering is attempted. Possible side-effects include complete destruction of the page, resulting in just the ad being shown (and no body content being visible).

Simply remove this call to resolve any issues related to use with Kiosked scripts.

### Disabling of Initial Load

Calls to GPT's [`disableInitialLoad`](https://developers.google.com/doubleclick-gpt/reference#googletag.PubAdsService_disableInitialLoad) require that new ad placements use the `googletag.pubads().refresh()` call to initiate them. While there are usually no problems using this with the Kiosked script, it is strongly recommended to not use this functionality.
