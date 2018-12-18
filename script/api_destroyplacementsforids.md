# destroyPlacementsForIDs

Destroy an array of placements by their IDs. Assuming that you have some placement IDs, you can pass them to `destroyPlacementsForIDs` and they will be destroyed. `destroyPlacementsForIDs` returns a `Promise`.

```javascript
Kiosked.API.destroyPlacementsForIDs(["...", "..."]).then(() => {
  console.log("All placements destroyed");
});
```

_It is not generally recommended to use this command in a **production** setting. If you wish to change your banner's behaviour, please contact your account manager._
