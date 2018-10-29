# getPlacementInfo

Get information about a placement by its ID. This function is synchronous.

```javascript
Kiosked.API.getPlacementInfo("k_12bd716bdd37c8118aaf7b5fa7715aea");
// {
//   alive: true,
//   container: ...,
//   context: "",
//   creationIndex: 0,
//   kioskID: "k_12bd716bdd37c8118aaf7b5fa7715aea",
//   loaded: true,
//   rendered: true,
//   scale: 0.67,
//   scalingEnabled: true,
//   secureMode: "extreme",
//   targetElement: ...,
//   type: "in-screen",
//   visible: true
// }
```

The method has the following signature:

`getPlacementInfo(placementID)`

| Parameter     | Type     | Required | Default   | Description               |
|---------------|----------|----------|-----------|---------------------------|
| placementID   | String   | Yes      |           | A Kiosked placement ID string. |

The return value is an object containing the details or `null` if no placement found.

You can use a function like [`getPlacementIDs`](script/api_getplacementids.md) to get an array of IDs.
