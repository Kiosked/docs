# onPlacementClose

Listen for the close event of a placement. Fires a callback when the selected placement is closed by the user.

```javascript
const kioskedAd = document.querySelector("p ~ div.kskdCls");
const placementID = kioskedAd.getAttribute("data-kioskid");
Kiosked.API.onPlacementClose(placementID, () => {
  console.log("Placement closed!");
});
```
