# Network logs using HAR files

[HAR files](https://blog.stackpath.com/glossary/har-file/) contain a log of network requests, their details and their content for a period of browsing activity. Typically they are recorded from the moment of **opening the developer console** (or page load, if the console was already open) to the time at which the user chooses to export the archive. They are incredibly useful for debugging network issues or for tracing unwanted content.

## Creating a HAR file

### Google Chrome instructions
For our example we'll be using Google Chrome to create a HAR file, but you can do this in most modern browsers.

Let's start by browsing to the page where we'll do the monitoring - we'll browse to [https://www.iab.com/news/](https://www.iab.com/news/) for our test. Once on the page, we'll want to open the browser's developer tools: **Menu > More Tools > Developer Tools**.

![The Devtools panel](/_media/debugging/har_devtools_open.jpg)

You'll want to head over to the **Network** tab in the devtools window. You may notice that it's currently empty or that it even has a couple of entries in it already. Regardless we'll want to refresh the page to get a full record of all the requests from when the page was actually requested.

After you refresh the page, you should see a large amount of requests in the network pane:

![The network panel requests list](/_media/debugging/har_network.jpg)

Once the event or issue that is being debugged is witnessed, it's time to export the HAR file. Right-Click anywhere within the list of network requests to bring up the following context menu:

![Exporting a HAR file](/_media/debugging/har_network_export.jpg)

After clicking "Save as HAR with content", Chrome will prompt you to save the file. Save it somewhere on your computer so that you can find it later to send to Kiosked.

### Safari instructions for creating a HAR file.

Open the Develop menu and select Show Web Inspector.
Click the Network tab and complete the activity that is causing issues.
Click the Export icon on the far right of the network tab and save the HAR file.

### Mobile Safari instructions.
1. Connect your mobile phone to computer with the compatible wire
2. Open Safari browser in both devices
3. Open the URL you want to debug on your Mobile Safari
4. On Desktop Safari go to Develop and select your phone from the list with the page you are browsing on mobile.

![Debug iPhone](/_media/debugging/debug_iphone.png)

5. Open the network tab on Desktop "web inspector".

![Mobile Safari Network](/_media/debugging/mobile_safari_network.png)

6. Browse with Mobile Safari on URL you want to debug and start browsing normally.
7. Browse site on your Mobile Safari until you get the malicious ad.
8. On Desktop web inspector choose "export" and save the HAR file.

![Mobile Safari Export](/_media/debugging/mobile_safari_export.png)


## Security precautions

HAR files contain almost all data that was sent during the period of time that the developer tools where open - this can include authentication information such as OAuth tokens and session cookies. Although we at Kiosked will always handle these files with care (and will dispose of them after the procesing), it is important to remember to **log out of all services** before undergoing this procedure. Using an Incognito session is advisable.

## Sending HAR files

HAR files can be incredibly large - sometimes in the 10s of megabytes. Please try to compress the file first (.zip is fine).

If the file is still simply too big to send (typically 10mb is the maximum you can send in an email), try a service like [WeTransfer](https://wetransfer.com/) or Dropbox (please alert your contact at Kiosked as to _how_ you sent the file).

## Viewing HAR files

You can preview the HAR file yourself if you like. Essentially the gigantic file is just text, but it contains many hundreds or thousands of blocks of request information which may be unwieldy in a text editor. Try an [online HAR viewer](https://ericduran.github.io/chromeHAR/) so that you can get a visual representation of the activity.

If you'd prefer a native application with which to peruse and debug HAR files with, try [Charles Proxy](https://www.charlesproxy.com/) (Paid).

WIP...
