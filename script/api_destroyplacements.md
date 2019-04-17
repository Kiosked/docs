# destroyPlacements

Destroy an array of placements by their IDs. Assuming that you have some placement IDs, you can pass them to `destroyPlacements` and they will be destroyed. `destroyPlacements` returns a `Promise`.

```javascript
Kiosked.API.destroyPlacements(["...", "..."]).then(() => {
  console.log("All placements destroyed");
});
```

_It is not generally recommended to use this command in a **production** setting. If you wish to change your banner's behaviour, please contact your account manager._

`destroyPlacements` takes a second parameter, `removeHash`, which is a boolean. It defaults to `false` but if set to `true` all of the hashes are removed from attactched items so that new placements can be automatically created.
