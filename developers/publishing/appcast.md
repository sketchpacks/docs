# Appcast Feeds

> From Sketch v45 onwards Sketch provides an officially supported mechanism for updating plugins within the app.

Sketch v45 onwards uses Sparkle Appcast feeds to update plugins. To take advantage
of native Sketch updates, you must provide an appcast file and include it in your
plugins manifest.

Sketchpacks can help automate this process by generating the appcast for you and
serving it from a HTTPS endpoint. To take advantage of the Sketchpacks Appcast
feed, add the appcast API endpoint for your plugin to the `appcast` property in
your manifest.

The Sketchpacks API endpoint for a plugins appcast is:

```
https://api.sketchpacks.com/v1/plugins/:identifier/appcast
```

For example, here is the manifest for the plugin [Copy Framer Code](https://sketchpacks.com/perrysmotors/copy-framer-code),
which is using the Sketchpacks appcast feed:

```json
{
  "name" : "Copy Framer Code",
  "identifier" : "com.gilesperry.copy-framer-code",
  "version" : "3.1.1",
  "homepage": "https://github.com/perrysmotors/copy-framer-code",
  "author" : "Giles Perry",
  "appcast": "https://api.sketchpacks.com/v1/plugins/com.gilesperry.copy-framer-code/appcast",
}
```

If you are using `SKPM` to build your plugins, you can set the `appcast` url in
the `package.json` instead of the `manifest.json`.  For example:

```json
{
  "skpm": {
    "name": "awesome-plugin",
    "title": "My Awesome Plugin",
    "manifest": "src/manifest.json",
    "main": "awesome-plugin.sketchplugin",
    "identifier": "my.awesome.plugin",
    "appcast": "https://api.sketchpacks.com/v1/plugins/my.awesome.plugin/appcast"
  }
}
```

## Managing your appcast feeds

Sketchpacks supports two workflows for building your plugins appcast feed. If your
plugin repository does not contain releases, then Sketchpacks will use the `push` workflow.
If your repository does contain releases, then Sketchpacks will use the `release` workflow.

> Tip: We recommended using `SKPM` and the `release` workflow to deliver your updates.

### Push Workflow

When you push to your default branch, Sketchpacks is notified and syncs with the
repository. To update your appcast, simply bump your plugin version and push the
change to your default branch.

This workflow works well in combination with `SKPM` or `Node.js` version bump commands.
However, you will only ever have one `HEAD` release in your appcast.  If you need
to support multiple versions for older Sketch clients, you will need to use the `release`
workflow instead.

> Note: Release notes are not available using the push workflow

For example, here is the appcast for [PDF export](https://sketchpacks.com/DWilliames/PDF-export-sketch-plugin),
which is using the `push` workflow:

```xml
<?xml version="1.0" encoding="utf-8"?>
<rss xmlns:sparkle="http://www.andymatuschak.org/xml-namespaces/sparkle" xmlns:dc="http://purl.org/dc/elements/1.1/" version="2.0">
  <channel>
    <title>PDF export</title>
    <link>
      https://api.sketchpacks.com/v1/plugins/com.davidwilliames.sketch.pdf-export/appcast
    </link>
    <description>
      Export artboards to PDF — from the current page, all pages or current selection
    </description>
    <language>en</language>
    <item>
      <title>2.1</title>
      <pubDate>2017-03-12 17:20:54 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.davidwilliames.sketch.pdf-export/download/update/0.0.0?range==2.1" sparkle:version="2.1"/>
    </item>
  </channel>
</rss>
```

### Release Workflow

When you create and publish new releases in your github repository, they will
automatically be added to your appcast feed. An easy way to do this is to
[use SKPM to publish your releases](https://github.com/skpm/skpm#publish-the-plugin-on-the-registry).

The release workflow is great for when you need to retain older versions for users
on old Sketch clients.  Also, it provides you with the ability to add change logs
in your appcast feed.

For example, here is the appcast for [Keys For Sketch](https://sketchpacks.com/exevil/Keys-For-Sketch),
which is using the `release` workflow:

```xml
<?xml version="1.0" encoding="utf-8"?>
<rss xmlns:sparkle="http://www.andymatuschak.org/xml-namespaces/sparkle" xmlns:dc="http://purl.org/dc/elements/1.1/" version="2.0">
  <channel>
    <title>Keys For Sketch</title>
    <link>
      https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/appcast
    </link>
    <description>Advanced shortcut manager for Sketch</description>
    <language>en</language>
    <item>
      <title>0.8.7</title>
      <description>- #23 Sketch v48 capability</description>
      <pubDate>2017-12-06 12:30:51 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.7" sparkle:version="0.8.7"/>
    </item>
    <item>
      <title>0.8.6</title>
      <description>Fixed:
       - Additional conflict resolving issues.</description>
      <pubDate>2017-10-18 18:42:02 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.6" sparkle:version="0.8.6"/>
    </item>
    <item>
      <title>0.8.5</title>
      <description>
      Fixed:
       - #16 Conflict resolution while search is used;
       - #19 #20 High Sierra related crashes.
      </description>
      <pubDate>2017-10-11 23:40:33 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.5" sparkle:version="0.8.5"/>
    </item>
    <item>
      <title>0.8.4</title>
      <description>
      Added:
       + #8 "Later" button into post-update alert.
      </description>
      <pubDate>2017-08-17 12:14:37 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.4" sparkle:version="0.8.4"/>
    </item>
    <item>
      <title>0.8.3</title>
      <description>
      Fixed:
       - #6 Canvas blinks on a start of editing text layers.
      </description>
      <pubDate>2017-08-17 12:14:37 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.3" sparkle:version="0.8.3"/>
    </item>
    <item>
      <title>0.8.2</title>
      <description>
      Fixed:
       - #3 Crash caused by wrong parsing of user keyboard layouts.
      </description>
      <pubDate>2017-08-15 11:48:29 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.2" sparkle:version="0.8.2"/>
    </item>
    <item>
      <title>0.8.1</title>
      <description>
      Fixed:
       - Some menus won't open its submenus;
       - Contextual menu indicator (▾) not disappearing when cursor leaves the cell.
      </description>
      <pubDate>2017-08-15 11:48:29 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.1" sparkle:version="0.8.1"/>
    </item>
    <item>
      <title>0.8.0</title>
      <description>Added:
       + #1 Search by menu title.</description>
      <pubDate>2017-08-14 14:30:23 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.8.0" sparkle:version="0.8.0"/>
    </item>
    <item>
      <title>0.7.0</title>
      <description>Initial release.</description>
      <pubDate>2017-08-09 23:46:27 UTC</pubDate>
      <enclosure url="https://api.sketchpacks.com/v1/plugins/com.vyacheslav-dubovitsky.KeysForSketch/download/update/0.0.0?range==0.7.0" sparkle:version="0.7.0"/>
    </item>
  </channel>
</rss>
```

#### Missing releases from your appcast?

Backfilling previous versions is done by [tagging a past commit](https://git-scm.com/book/en/v2/Git-Basics-Tagging#_tagging_later) in your history.

Say for example, you forgot to tag your plugin at `v1.2.3`, which was a fix for some bugs. Just find the commit checksum (or SHA) where you commited the fixes (e.g. `9fceb02`), and specify it at the end of the `tag` command.

```
$ git tag -a v1.2.3 9fceb02
```

Now push those commits to Github and begin [drafting and publishing your releases](https://help.github.com/articles/creating-releases/).

```
$ git push --tags
```

By publishing your releases, they'll immediately become available from your plugin's Appcast feed URL.

---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/appcast.md).
