# Blocking ad placements

It's possible to block ads on certain elements, either by contacting Kiosked directly or by modifying website pages directly.

## Blocking ads on elements

If there are certain elements or groups of elements that should be blocked when ad placements are being created, a simple CSS class can be added to tell Kiosked scripts to avoid them: **.kskddisable**

For example, one element is blocked in the HTML below:

```html
<div class="someContent"></div>
<div class="social kskddisable">
  <img src="..." />
</div>
<div class="otherContent"></div>
```

The element in the middle, with the `social` class, is blocked and no ads will be created on it. The `<img>` tag within it is also blocked.


## Avoiding areas of the page

Sometimes there are sections of the page that should be avoided - for instance, some social buttons might need some area around them where no ads can be created to ensure clear accessibility for the users. While disabling the elements exactly using `.kskddisable`, disabling elements on different hierarchical levels may be impossible.

Although it isn't currently possible to do this from the publisher side, it can be requested as a feature from Kiosked staff. _Avoidance settings_ can be applied to a script to avoid elements and the _area around them_ quite easily.
