# GDPR & Cookie Consent

The Kiosked monetization script has built-in functionality for detecting the location from which the user is browsing a site, and will automatically configure **user consent handling** when making requests to our demand partners. The script will automatically detect and request consent from on-page CMPs (Consent Management Platforms), passing these on to the relevant networks when auctions are performed on inventory.

## Who Needs a CMP?

**Everyone** needs a CMP, especially those with any amount of European traffic. Traffic from the EEA is bound by law to request consent from the user when tracking of any kind is to be enabled. Many demand partners support tracking when enabled, and all support bidding without tracking (even though monetization is usually substantially less effective). Using a CMP to gather user consent will improve monetization efforts and is **highly recommended**.

### What CMP should I use?

A CMP should conform to [IAB standards of consent](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/), as well as [guidelines provided by Google](https://www.cookiechoices.org/). An easy choice here is [Quantcast's Choice](https://www.quantcast.com/blog/quantcast-choice-your-solution-for-gdpr-consent/), a well-built and popular CMP that supports both standard IAB consent _and_ Google personalization consent out of the box. Kiosked recommends the use of Quantcast's CMP as we have direct integration with it without the need for any modifications.

## Setting up a CMP

Whatever CMP you use, you should reach out to your Kiosked account manager to discuss its compatibility with our platform. If it's a new CMP we haven't integrated with, we'll prioritize compatibility with it so we can support your site(s). The CMP _must_ support Google personalization consent. Your account manager will need to send you a **static vendor list** for you to connect to your CMP's Google consent.
