# Placements

Placements are individual ad containers (inventory) that the Kiosked scripts place/render on a page. Each placement represents a functional component of the Kiosked platform that manages its own:

 * Demand mediation
 * Analytics events
 * Backfill and self-destruction
 * Refreshing
 * Viewability detection

A [static tag](script/introduction_statictag.md) is a 1:1 script which creates a single placement instance, exactly where the script element is placed in the DOM. A [dynamic script](introduction_dynamic.md) can create many placements, wherever configured. A placement created by a static tag and that of a dynamic script are mostly indistinguishable. 

## Anatomy of a placement

A placement will feature a single root `<div>` element which will contain all of the ad content and other elements necessary for operation. Inside this root element will be, in no explicit order:

 * A visibility-tracking `<div>`
 * The disclaimer (if enabled): The Kiosked ads disclaimer message and close button
 * Various rendering containers for handling the visibility of the ad
 * Ad containers
 * Ad contents
 * Piggyback/tracking pixels from header bidding auctions

## Valid operating environment

A placement needs to be in a location on the page that will be visible - it should not be contained within a hidden/invisible container or inside a non-visual element (like `<table>`, `<ul>` or `<head>`, for instance). The containers above the placement should not be smaller than the resulting ad, and should never be 0 pixels in width or height.

### Reloading of DOM contents

Some widgets or web tools, like jQuery, allow for _wrapping_ elements in new containers - This is discouraged as it breaks many elements contained within the wrapped element, including Kiosked placements. Take the example below:

![Example ad setup](/_media/validplacement_wrap_eg1.jpg)

A common problem with sites that use wrapping techniques to insert elements above others in the DOM tree is that they wrap elements quite late and that already contain processed content like videos and iframes. In the example above, Kiosked has rendered an ad placement below an image - if the wrapping library were to wrap the *container* element:

![Example ad setup after wrapping](/_media/validplacement_wrap_eg2.jpg)

Then the Kiosked placement would have been broken by the wrapping procedure. A wrap procedure normally _removes_ an element from the document, adds the new parent, and then adds the original element as a new child to the new parent. By removing any element from the DOM, it's more complex contents are *reset*. `<iframe>` elements, especially those with dynamically added content (that Kiosked and many other ad networks rely on), are rendered blank by this process.

It is strongly recommended that you speak to your account manager or Kiosked support if you know of such a procedure taking place on your site. For a placement to work on a site that uses wrapping, either the placement needs to be placed outside of such areas that are wrapped, or the wrapping needs to be removed from the site.
