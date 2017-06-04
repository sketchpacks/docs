# Appcast Feeds

> From Sketch v45 onwards Sketch provides an officially supported mechanism for updating plugins within the app.

To have the Sketchpacks API serve your appcast feed, reference the plugin by identifier for the `appcast` key in the `manifest.json`.

```
https://api.sketchpacks.com/v1/plugins/IDENTIFIER/appcast
```

Here's an example of [Copy Framer Code's manifest.json](https://github.com/perrysmotors/copy-framer-code/blob/master/CopyFramerCode.sketchplugin/Contents/Sketch/manifest.json#L9) using the Appcast API endpoint.

```
{
  "name" : "Copy Framer Code",
  "identifier" : "com.gilesperry.copy-framer-code",
  "version" : "3.1.1",
  "homepage": "https://github.com/perrysmotors/copy-framer-code",
  "author" : "Giles Perry",
  "appcast": "https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/appcast",
  // ... reduced for brevity
}
```

Viewing the raw body of the Appcast API endpoint provides a similar XML shape as the one below.

```

<?xml version="1.0" encoding="utf-8"?>
<rss xmlns:sparkle="http://www.andymatuschak.org/xml-namespaces/sparkle" xmlns:dc="http://purl.org/dc/elements/1.1/" version="2.0">
  <channel>
    <item>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/download?version=3.1.1" sparkle:version="3.1.1"/>
    </item>
    <item>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/download?version=3.1.0" sparkle:version="3.1.0"/>
    </item>
    <item>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/download?version=3.0.1" sparkle:version="3.0.1"/>
    </item>
    <item>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/download?version=3.0.0" sparkle:version="3.0.0"/>
    </item>
    <item>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/download?version=2.0.1" sparkle:version="2.0.1"/>
    </item>
    <item>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/download?version=2.0.0" sparkle:version="2.0.0"/>
    </item>
  </channel>
</rss>

```

The `<channel>` enumerates each of [Copy Framer Code's releases](https://github.com/perrysmotors/copy-framer-code/releases) from Github with version specific download URLs for each enclosure.
