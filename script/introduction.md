# Introduction

The publisher monetization, also known as the Kiosked client library, is a JavaScript client that is loaded by publishers to perform banner creation and mediation on their site. The scripts are delivered as HTML (JavaScript _tags_) and are normally inserted into the `<head>` (except [static tags](script/introduction_statictag.md)).

## Serving Kiosked scripts

The client library scripts should be embedded on the publisher's webpages and subsequently loaded by the users' browser. By mentioning the `<script>` already in the page's HTML template, the scripts will be downloaded and executed in the most efficient manner possible by the browser.

It is possible to load Kiosked scripts via a 3rd-party system, such as _DFP_, but this is **not recommended**. Using JavaScript-based systems, such as DFP, to load Kiosked scripts will **substantially decrease overall performance**.

### Caching

Kiosked scripts are cached in an intelligent manner, and no further caching practises are necessary. Adding a _cachebuster_ to the client scripts is **unadvisable** and will cause a decrease in overall performance and may result in the account being deactivated.

The client scripts are cached via a multi-endpoint highly available CDN service. The CDN responds with specific HTTP response codes to allow the browser to cache for a longer period of time while lightly checking for updates in the background.

## Types of scripts

There are 2 primary types of scripts provided by Kiosked:

 * [Dynamic](script/introduction_dynamic.md) scripts are smart payloads that generate _several_ ad placements per page.
 * [Static](script/introduction_statictag.md) tags are scripts which generate a single placement per instantiation, and closely resembles standard industry ad tags.

For monetization purposes, the **dynamic script** is the preferrable option. Static tags are provided merely for compatibility reasons.
