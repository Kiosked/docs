# How AMP works

AMP stands for **Accelerated Mobile Pages**, and is a Google initiative to improve mobile website responsiveness and performance by heavily restricting what resources can be loaded in an AMP environment. [AMP pages](https://www.ampproject.org/) are available on many publisher websites and are preferred when using browsers like Google Chrome for mobile.

If you're not sure whether or not your site is AMP-ready, drop one of your URLs into the [AMP Test](https://search.google.com/test/amp) page. If you'd like to learn how to set up AMP on your site, check out the [Creating AMP pages](#creating-amp-pages) section.

## Kiosked Compatibility

Kiosked ads are compatible with AMP - Kiosked "static tags" work just fine in an AMP environment. Check out the [AMP Ads](script/amp_ads.md) page.

## Creating AMP pages

Creating AMP pages is **not super easy** if you are adding it to your site, rather than building with AMP in mind. This is because many elements are not allowed and others need to be converted to correct AMP counterparts (like `<img>` and `<amp-img>`). That being said, it is indeed possible but it'll take some work. This guide will prove as a kick-start for getting the AMP process started.

> Before diving in, it's advisable to get set up with Google Chrome and the [AMP Browser Extension](https://chrome.google.com/webstore/detail/amp-browser-extension/mccnchmofleakpdohkmljohfckgpdehb?hl=en) - These are necessary for testing AMP pages. The extension will help you identify if you've gotten AMP working correctly or not. Don't forget to use the [AMP Test](https://search.google.com/test/amp) tool once your pages are live!

Let's use an example to explain AMP functionality - say you have a page with the URL `https://mywebsite.com/articles/some-topic`: This page would serve your **standard HTML/webpage** as it does today. AMP pages are _usually_ **entirely separate pages** (Kiosked recommends keeping them separate), and the AMP counterpart to this example URL might me `https://mywebsite.com/amp/articles/some-topic` or even `https://amp.mywebsite.com/articles/some-topic` (notice the `/amp/` and `amp.` additions respectively).

On an AMP page there are several things which happen in addition to your standard webpage logic:

 1. The document is flagged as being an AMP document in the source: `<html amp>` or `<html ⚡>`
 2. The canonical URL for the page is mentioned as a way to _link back_ to the standard page (non-AMP)
 3. AMP-required styles are applied
 4. Mobile viewport settings are specified
 5. AMP-incompatible items are converted to AMP-compatible ones or removed entirely

> This list is non-exhaustive - please check out the [required AMP mark-up](https://amp.dev/documentation/guides-and-tutorials/start/create/basic_markup/?format=websites#required-mark-up) for what's required.

You should be aware that AMP pages are drastically stripped-down versions of the original content, for mobile browsers, so starting with a clean template is recommended. It'd be much more simple to start from a blank document and build the AMP version of your website (in most cases) than it would be to strip down to an AMP version. Many scripts (especially advertising libraries) will simply not work (be advised that **Kiosked's scripts (static) will function just fine**), and many media-rich elements may need to be changed or removed.

### AMP Pages Demonstration

Kiosked hosts an AMP sandbox site for demonstrating how AMP works in its most simple form:

 * Standard non-AMP URL: [http://research.kiosked.com/ampdemo/](http://research.kiosked.com/ampdemo/)
 * AMP-enabled URL: [http://research.kiosked.com/ampdemo/index-amp.html](http://research.kiosked.com/ampdemo/index-amp.html)

When browsing to the non-AMP URL with the **AMP Browser Extension** installed and enabled you might notice that you're redirected immediately to the AMP version. This is a good sign as it means that the extension recognised that AMP is available. When testing the AMP page you should open the Developer Console (`Shift + Ctrl + I` _or_ `Command + Option + I`) and toggle the mobile emulator function so that you can view your website as if from a mobile browser.

![AMP development testing using Chrome](/_media/amp_ads/amp-dev-switch.gif)

Dive in to the source code of these so you can see how they link to each other, how the AMP-enabled page bootstraps itself and how _easy it is_ to get going with AMP. Viewing the source of the `index-amp.html` page will show you how to embed Kiosked static tags (as AMP tags) within your AMP pages.

> Remember that AMP tags, such as the Kiosked `<amp-ad>` tags, are **not supported** within standard non-AMP pages.
