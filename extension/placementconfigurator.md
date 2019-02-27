# Placement Configurator Extension

> The Placement Configurator Extension is a tool for creating advertising layouts within websites and their pages using the Kiosked PMP framework.

## Download

The extension is freely available to install in your browser:

 * [Chrome](https://chrome.google.com/webstore/detail/kiosked-placement-configu/fainllnembbdgheolobpcciomhogojdf)

## Usage

While the extension is running (and enabled via the menu), existing Kiosked scripts are blocked so that users can concentrate on the configuration provided by the extension. Disabling this setting will revert back to any live script running on the site.

_After installing the extension you will need to refresh the page that you wish to start configuring so that the extension can correctly attach to it._

You can create multiple configurations before enabling them.

### Controlling the extension via the menu

![Extension with a single item added](/_media/extension/extension_2.png)

 * The `Add` button creates a new placement that can be run on the current page
 * The `Enable` button enables/disables the execution of the extension
 * `Save` saves the configuration - reserved for future use.

Each placement can be enabled or disabled using the checkbox on the left-side, and whole placements can be removed using the `X` on the right-side.

When a new placement is created, you can straight away configure the type (refer to the different [placement types available](script/placementtypes.md)) and size.

#### Selecting an element

When a new placement is created, use the `Select` button to select the element on the page to attach the placement to. Kiosked placements are primarily attached to existing page structures.

_Note that if you're creating an **in-screen** placement, the `Select` button will not be available as the placement attaches to the screen border._

After clicking the desired element, the configuration will be updated to match the CSS selector of the element you chose. This CSS selector will appear in the button instead of the `Select` text. You can click it again at any time to change it.

![Multiple items with different selected elements](/_media/extension/extension_5.png)

#### Changing the ad frequency

Beside the `Select` button lies a frequency control. Clicking this button provides an interface for configuring how often banners are shown on this selector.

Selectors will often provide more than 1 element, and Kiosked supports creating multiple banners using a single selector. Typically all elements under a selector may be chosen to create banners, but this behaviour can easily be changed here. There are several types available:

 * `all` - Create banners on all possible elements
 * `first` - Create banners on the first (or first n) elements
 * `last` - Create banners on the last (or last n) elements
 * `every` - Create banners on every 2nd element, for example (step, offset and maximum can also be configured)

![Configuring different frequencies](/_media/extension/extension_6.png)

#### Configuring other options

Other options are available, per placement, under the far-right settings button. Features such as the visibility of the disclaimer bar or the unit's scaling can be controlled here.

## Troubleshooting

If you encounter any issues while using the extension, please contact your account manager.
