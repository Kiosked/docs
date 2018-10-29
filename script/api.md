# Monetization Script API

The publisher script comes with an API (only in the dynamic version) that can be accessed via the global `window` object. The API allows for some control over the script, but cannot be used to perform large-scale placement creation and configuration.

The API should be used by **Kiosked staff only**, but documentation is provided here for one-time use by publishers who are debugging their pages.

## Usage

When running a [dynamic script](script/introduction_dynamic.md), the API can be accessed via `window.Kiosked.API`. This will be referred to in short as `Kiosked.API`.

The following methods are available:

 * `Kiosked.API`
   * [`onElementInteraction`](script/api_onelementinteraction.md)
   * [`onElementsInteraction`](script/api_onelementsinteraction.md)
