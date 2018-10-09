# Static tags
> Industry standard single-ad placement generation script

Static tags are simple scripts that create a single ad placement in the **same location that the `<script>` tag is placed**. They can be loaded many times per page, even using the same ID. The URL should not be modified before placement, and there is **no need for a cachebuser**.

Static tags will appear like the following:

```html
<!-- Begin Kiosked Ad -->
<script type="text/javascript" src="//scripts.kiosked.com/loader/kiosked-ad.js?staticTagId=STATICTAGID"></script>
<!-- End Kiosked Ad -->
```

## Placement

Static tags, as mentioned above, create ads exactly where they're placed. They should be placed within the `<body>` block in a location that is visible to the user and not obscured by any other element.

## Static vs Dynamic

The [dynamic script](script/introduction_dynamic.md) is a more lightweight and speedy alternative to static tags and is definitely the preferred method of monetization. Static tags are provided merely for compatibility reasons or when the top-frame of a webpage is not accessible.

## Injection

Static tags are normally provided as HTML snippets that should be rendered in the body along with the rest of the web page. If being injected from an ad server, it is important that the server is capable of writing executable HTML to the page using `document.write` or some other method. Scripts inserted by ad servers should be executable.

It is also possible to inject by running a JavaScript snippet, which may appear like the following:

```javascript
(function(doc, target) {
var s = doc.createElement("script");
s.src = "//scripts.kiosked.com/loader/kiosked-ad.js?staticTagId=STATICTAGID";
target.parentElement.insertBefore(s, target.nextElementSibling);
})(window.document, targetElement);
```

_In this example, `targetElement` is the element where the static tag will be inserted **after**._

### HTML embedding vs. ad server injection

It is desirable to always embed static tags within the rendered HTML of the page. Using an ad server's containers will result in **blank ad placements** when there isn't any fill available. Kiosked placements, including the static tag, will automatically close and clean up when there is no demand - if contained within a generated placement container that was created by an ad server, this outer container will not be closed and will instead leave unwanted black space.

If using an ad server is absolutely necessary, it is recommended that no containers be used on the ad server side so that the static tag is simply injected into the body.
