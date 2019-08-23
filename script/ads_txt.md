# Kiosked ads.txt

The use of the Kiosked monetization script requires an `ads.txt` file to be placed at the **root** of your website, containing the appropriate demand entries mentioned below. If you own the site `https://example.com`, your ads.txt file would be accessible at `https://example.com/ads.txt`.

Ads.txt items are basically permissions for each demand source to _buy inventory_ from your site - By adding items here you're allowing that network to place ads on your site. Kiosked requires that you add its items to your `ads.txt` file so that its provided ad demand will function correctly.

## ads.txt contents

When creating your `ads.txt` file, enter the contents provided to you by your Kiosked contact. All `ads.txt` files are **unique** per client and cannot be shared. Please do not copy any `ads.txt` lines from any other site.

Make sure that you edit your `ads.txt` file with a **plain-text editor** so as to not corrupt the file with invalid formatting (Microsoft Word or Wordpad will usually not save in plain-text format and will usually result in corrupted `ads.txt` files).

If you have existing contents in this file **not** from Kiosked, you can append Kiosked's items to the end of the file.

## ads.txt updates

After some time your Kiosked contact may ask you to update the items in your `ads.txt` file with the latest copy visible above. Because of this, it's wise to separate your `ads.txt` into groups if you use more than one service provider like Kiosked. One example of this grouping might look like the following:

```
# Network 1
some.service.com, 12345, DIRECT
another.service.com, 67890, DIRECT

# Home items
google.com, pub-0000000000000, DIRECT, aaaabbbbbcccc

# Network 2
network1.org, abc123, RESELLER

# Kiosked
# ...
```

This way, when you need to update just Kiosked's items, you can select the whole group, delete it, and then paste a new copy of the lines from above.

## Validating your ads.txt

You can use an [`ads.txt` validator](https://www.adstxtvalidator.com/) to validate your file. Don't worry about messages regarding some exchanges that aren't recognised, as this is a common issue, but make sure that the file is formatted correctly and that there are no critical errors.
