# Compatibility

As the Kiosked script is usually run in a shared environment, potentially alongside other analytics / advertising scripts, some compatibility factors should be considered.

## Existing Google Ads (DFP / GAM)

If you already use Google ad demand on your site, you'll most likely be initiating calls to Google via Google Ad Manager (formerly DFP). As Kiosked scripts also provide Google ad demand, there are a few rare issues that may occur when running both side-by-side.

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
