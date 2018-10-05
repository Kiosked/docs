# Placement SecureMode

Kiosked ad placements can be rendered using a variety of containers on most modern browsers (including IE10 and above). Different rendering and framing techniques are used for different networks, different sites and different geographical regions.

One of the most common methods of rendering ads within placements is of course `<iframe>` elements. Iframes make for a great container for ads so that their resources are held separate to the parent page. Not only does this prevent style leaks, but can also help reduce JavaScript interface incompatibilities when running our script across thousands of different sites.

It’s unfortunately impossible to control the output of each demand request to the extent that safety against fraudulent advertisers can be 100% guaranteed, so a safe-frame technique has been employed to prevent scripts from accessing the parent frame (`window.top`).

Kiosked’s `<iframe>` rendering functionality comes in 3 forms:

 * No sandboxing (default): Regular iframe which contains the mediated ad item.
 * Secure Mode: HTML5 Iframe sandboxing attributes applied, preventing top page navigation.
 * Extreme Mode: Restrictive Iframe sandboxing with complete lockdown (no JS access to parent page).

Usually no sandboxing or sandboxing with secure mode are the methods used when rendering iframes, but extreme mode is used on occasion to ensure that there is no access to the publisher’s website.

## SecureMode (light sandboxing)

When secure mode is activated, HTML5 sandbox attributes are applied to the placement container to enable restrictions on the rendered ad content.

```html
<iframe
   src="about:blank"
   sandbox="allow-forms allow-popups allow-popups-to-escape-sandbox allow-scripts allow-same-origin"
   />
```

These sandbox attributes indicate allowed features, and all other [HTML5 sandbox attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-sandbox) are disallowed. Kiosked allows only the most necessary features for ads to function correctly and viewability/impression pixels to fire.

### Vulnerabilities protected against

Secure mode protects the user browsing the page from fraudulent ads that aim to manipulate the browser session to redirect or trick the user by triggering various browser features. Some items which are prevented are:

 * Sending the browser into presentation mode
 * Redirecting the user from the page to some other malicious site
 * Trapping the cursor/focus within the ad container
 * Locking the mobile device screen orientation
 * Opening modal windows without user action

By using a lighter form of protection there are unfortunately some **minor drawbacks**, such as the following vulnerabilities which are not defended against effectively:

 * Inserting JavaScript into the top window
   * Redirecting the page once JS is injected
   * Removing HTML5 sandbox attributes on the protected iframe

These drawbacks are generally not often utilised by fraudulent players and the lighter secure mode is considered acceptable for the majority of publishers.

## ExtremeMode (heavy sandboxing)

Extreme mode is Kiosked’s final-word in terms of protecting the publisher’s page from any rogue advertisements. The sandboxing used in this mode is, by our definition, extreme - It’s heavily restrictive and basically allows for safe-frame style operation as if the content was being served from another domain. This has the benefit that it’s both treated as _remote content_ while still being loaded locally (no bandwidth spent on requests to remote pages for the sake of the sandboxing).

This mode works by setting HTML5 sandbox attributes, similar to the lighter secure mode, but without the `allow-same-origin` flag. This effectively removes any opportunities that the scripts within the ad would have had to reach the top frame of the page. Once this flag is removed, however, more advanced frame invocation is required.

```html
<iframe
   src="about:blank"
   srcdoc="<script>document.open(); document.write(decodeURIComponent(atob('JTNDc3R5bGUlMjB0eXBlJT..."
   sandbox="allow-forms allow-popups allow-popups-to-escape-sandbox allow-scripts"
   />
```

Notice the srcdoc attribute in the example above - it’s required to be able to inject the ad content into the frame, due to the dissimilar origins. The advertising content is base64 encoded and piped into the highly-secured iframe, being rendered by the `document.write` statement in a synchronous manner (improved speed).

The following example shows a live banner being rendered into an extreme-mode secured frame:

![Extreme mode Iframe (start)](/_media/securemode/iframe_extreme_start.png)

![Extreme mode Iframe (end)](/_media/securemode/iframe_extreme_end.png)

The ad still renders successfully but has no ability to affect the user’s browsing session, thus thoroughly protecting the user against any potentially malicious ads.

## HTML Sandbox attributes

The following attributes are recognised by Kiosked placements:

| Attribute Name | Allowed in SecureMode | Allowed in ExtremeMode | Description |
|----------------|-----------------------|------------------------|-------------|
| `allow-forms`  | ✔                     | ✔                      | Allow HTML forms to be created within the placement. |
| `allow-modals` | ✘                     | ✘                      | Allow modals to be created from within the placement. |
| `allow-orientation-lock` | ✘           | ✘                      | Allows the embedded content to control the device orientation lock. |
| `allow-pointer-lock` | ✘               | ✘                      | Allows the embedded content to access the Pointer Lock API. |
| `allow-popups` | ✔                     | ✔                      | Allows calls to methods like `window.open()` to create popup windows. |
| `allow-popups-to-escape-sandbox` | ✔   | ✔                      | Allows popup windows to be created that do not have the HTML5 sandbox flags set. |
| `allow-presentation` | ✘               | ✘                      | Allows the embedded content to enter presentation mode. |
| `allow-same-origin` | ✔                | ✘                      | Treats the ad within the placement to be treated as being from the same origin as the parent page. |
| `allow-scripts` | ✔                    | ✔                      | Allows the execution of JavaScript within the placement. |
| `allow-top-navigation` | ✘             | ✘                      | Allows the embedded ad to trigger a navigation on the top frame. |
| `allow-top-navigation-by-user-activation` | ✘ | ✘               | Allows the embedded ad to trigger top-frame navigations when initiated by a user gesture. |

**NB**: If a HTML5 sandbox flag is not mentioned here, it is by default _blocked_. There is no security risk missed due to unimplemented or unrecognized flags.
