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

### Missing a previous version?

Backfilling previous versions is done by [tagging a past commit](https://git-scm.com/book/en/v2/Git-Basics-Tagging#_tagging_later) in your history.

Say for example, you forgot to tag your plugin at `v2.0.0`, which was fixing Bug A. Just find the commit checksum (or SHA) where you commited the fix for Bug A (e.g. `9fceb02`), and specify it at the end of the `tag` command.

```
$ git tag -a v1.2 9fceb02
```

**Note:** The `version` key's value defined within your plugin's manifest should match your lightweight or annotated tag.

Now push those commits to Github and begin [drafting and publishing your releases](https://help.github.com/articles/creating-releases/).

```
$ git push --tags
```

By publishing your releases, they'll immediately become available from your plugin's Appcast feed URL.
