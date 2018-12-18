# getBannerStatus

Get the status of an element's Kiosked banner. Pass in the element that an ad placement was **attached to**.

Such an element may look like the following:

```html
<p
  kioskedhash_production="11277_25bc45585039b99f1985ae2b448ac0f4"
  data-kiosked-context-name="kskdUIContext_6edbc8a1c2373ef192204f0794fe9615"
>
  ...
</p>
```

You can pass this element to `getBannerStatus`:

```javascript
Kiosked.API.getBannerStatus(myPTag); // "destroyed"
```

The following values are returned:

 * "active": The placement is currently alive and well
 * "inactive": The placement is alive but is not currently showing a banner
 * "destroyed": The placement has pass-backed and has been destroyed
