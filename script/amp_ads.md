# AMP Ads

AMP ads are ad placements that execute within an AMP context, and are generally heavily sandboxed in terms of JavaScript execution and DOM access. [AMP pages](https://www.ampproject.org/) are available on many publisher websites and are preferred when using browsers like Google Chrome for mobile.

## Kiosked Compatibility

Kiosked ads are compatible with AMP - but only a smaller subset of the tags that we provide will work. Dynamic tags **will not work**, whereas **static tags will function fine** if formatted as an AMP-friendly HTML block.

## Creating AMP ads from Kiosked tags

Having been given a static tag code block from a Kiosked representative, you'll find it looks similar to the following:

```html
<!-- Begin Kiosked Ad -->
<script type="text/javascript" src="//scripts.kiosked.com/loader/kiosked-ad.js?staticTagId=STATICTAGID"></script>
<!-- End Kiosked Ad -->
```

AMP ads are much simpler, and the example above will end up looking like the following in an AMP setting:

```html
<amp-ad
  width="300"
  height="250"
  type="kiosked"
  data-scriptid="STATICTAGID">
</amp-ad>
```

Notice the `width` and `height` properties: These must be set to the correct size as instructed by Kiosked. Setting these values incorrectly will result in incorrectly displayed ads and potential loss of revenue.

## Usage with other ad formats

Kiosked AMP ads work fine with other unit styles, such as the [flying carpet](https://ampbyexample.com/components/amp-fx-flying-carpet/) format. You can simply nest the Kiosked `amp-ad` element within the unit in most cases:

```html
<amp-fx-flying-carpet height="300px">
  <amp-ad
    width="300"
    height="600"
    type="kiosked"
    data-scriptid="STATICTAGID">
  </amp-ad>
</amp-fx-flying-carpet>
```
