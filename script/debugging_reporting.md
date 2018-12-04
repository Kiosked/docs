# Reporting issues

When reporting issues to your account manager or representative, it's important to include enough information regarding the issue for someone to be able to help you as quickly as possible. If the issue is technically complex, your account manager may forward the issue directly to our engineering team for a quick fix - having all the details necessary to debug the problem may help solve the issue in a much shorter period of time.

Here are some details to include in such reports:

 * The **URL** where the issue was detected
 * The device on which the issue was detected
 * The browser used
 * Geographic location when the issue was detected
 * Exact steps to reproduce the issue

Providing a story that describes how to reproduce the issue is a great way to communicate exactly what's going wrong. It can even substitute a formal description in many cases. Here's an example:

> Browse to `http://test.com/page.html` and wait for it to load. Very quickly scroll to the bottom of the page and wait for the infinite scroll to load. Once loaded, scroll quickly to the bottom once again. Notice that the loader stays visible and no further infinite-scroll content is presented.

Screenshots of the issue are also very useful - They can help engineerings quickly determine if the issue is a known problem or something entirely new. Don't worry about providing too many or being too thorough with your report as more information is always appreciated.

## Providing network logs

If the issue concerns invalid traffic, malicious ads or unwanted advertisements, a network log may be required. Such logs contain a wealth of data in terms of what media (images, video etc.) were loaded by whom. You can follow the [HAR creation guide here](script/debugging_har) to create a HAR (network log) file which can be shared with Kiosked staff.
