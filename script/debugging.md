# Debugging

There are a variety of situations where script functionality can be hindered by other scripts and page layouts. There is also the potentiality of a placement rendering a _malicious_ advertisement that tricks the user or interrupts their interaction with the site.

This section details common issues and some ways to combat them.

## No ads appearing

When using the dynamic script, which creates multiple ad placements per load, the sight of no ads being created once run can be concerning. If the script is a brand new one, which may still be in its testing phase, it's possible that one of the following issues may be responsible:

 * Incorrect/Incomplete targeting on the Kiosked side
 * The current page doesn't have any targeted elements
 * The script cache has not yet cleared and the configuration is still pending (cache can take up to about 20-30 minutes to clear)

If you believe the placement of the `<script>` tag to be correct, then you should contact your Kiosked representative.

If none of these are applicable, the location of the `<script>` tag may be incorrect:

 * If you are using DFP or another ad server to _inject_ our script, you should read the [injection via an ad server](script/introduction_dynamic?id=injection-via-an-ad-server) section.
 * If you are using a **static tag**, make sure that it's placed in the `<body>` of your site in an area which is visible and without complex CSS rules potentially obscuring it.
 * Make sure that the HTML code of the tag is formatted correctly - copying it from a Word document or email can sometimes result in the quotation marks `"'` being rendered in a _pretty_ format `“‘` which does not work in the browser.
 * If possible, check the [Developer Console](https://developers.google.com/web/tools/chrome-devtools/console/) to see if any errors are displayed there. It might be that the browser can explain exactly what's going wrong.

If all else fails please reach out to your account manager at Kiosked - We'll do our best to remedy the situation as quickly as possible. Please read our [issue reporting guidelines](script/debugging_reporting).

## Unwanted ads

If you see an ad that you feel is offensive or suggestive, you should report it immediately to Kiosked personnel. Please note that not all advertisements can or should be blocked - the process is very resource intensive and may take some time to undertake.

To request the blocking of some advertisement, Kiosked personnel need some details as to where the ad came from. Please read the [reporting guidelines](script/debugging_reporting) before submitting an issue. To successfully block an ad we'll also need some more details regarding the placement:

 * The filename/URL of the image
 * The HAR network log of that page load

To collect the network log, follow the [HAR file creation documentation](script/debugging_har).

To find the URL of the image, Right-Click on the ad's image and select "Inspect":

![Inspect an element](/_media/debugging/debugging_inspect.jpg)

This will display the element's HTML in the inspection pane:

![Inspecting an element](/_media/debugging/debugging_inspected_element.jpg)

You can then Right-Click on the image and copy its URL:

![Copy an image's URL](/_media/debugging/debugging_img_copy_url.jpg)

Send this URL along with the HAR file to your Kiosked representative.
