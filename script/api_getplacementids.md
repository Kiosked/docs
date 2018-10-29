# getPlacementIDs

Get an array of active placement IDs. Placements (or ads) can be handled by their **placement ID**, and this method returns an array of current IDs that are in use on the page.

```javascript
Kiosked.API.getPlacementIDs(); // ["k_12bd716bdd37c8118aaf7b5fa7715aea"]
```

The function is synchronous and returns an array of strings or an empty array.
