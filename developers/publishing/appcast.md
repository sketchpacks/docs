# Appcast Feeds

> From Sketch v45 onwards Sketch provides an officially supported mechanism for updating plugins within the app.

Sketch v45 onwards uses Sparkle appcast feeds to update plugins. To take advantage
of native Sketch updates, you must provide an appcast file and include it in your
plugins manifest.

Sketchpacks can automate this process for you by generating, maintaining, and
serving your plugins appcast feed to the Sketch community. The appcast feed also
helps provide some insight into your plugin's user activity and retention.

## Appcast Essentials

* you must provide a `HTTPS` url to your `appcast.xml` file
* you must define the `appcast` property in your `manifest.json`
* you may optionally define your `appcast` in your `package.json`

## Appcast Setup

1. ensure your plugin meets [the essentials for Sketchpacks](./essentials.md)
2. set the `appcast` property in your `manifest.json` or `package.json` to the
Sketchpacks appcast url for your plugin
3. (optional) add your plugin's `appcast.xml` file path to the `.sketchpacks/settings.json` file.

> **Note**: If you do not want Sketchpacks to generate your appcast feed,
you can serve an appcast.xml file from your repository instead!

Below is the endpoint for the Sketchpacks appcast feed.  Replace `:identifier` with
your plugin's [unique identifier](./identifiers.md).

```
https://api.sketchpacks.com/v1/plugins/:identifier/appcast
```

### Setup Examples

Example `manifest.json`:

```json
{
  "name" : "My Awesome Plugin",
  "identifier" : "my.awesome.plugin",
  "appcast": "https://api.sketchpacks.com/v1/plugins/my.awesome.plugin/appcast"
}
```

Example `package.json` if you are using `SKPM`:

```json
{
  "skpm": {
    "name": "awesome-plugin",
    "title": "My Awesome Plugin",
    "manifest": "src/manifest.json",
    "identifier": "my.awesome.plugin",
    "appcast": "https://api.sketchpacks.com/v1/plugins/my.awesome.plugin/appcast",
    "main": "awesome-plugin.sketchplugin"
  }
}
```

## Managing your appcast feed

Sketchpacks supports two workflows for building your plugins appcast, the `push` and
`release` workflows. If your repository contains releases, Sketchpacks will use the
`release` workflow.  Otherwise the `push` workflow will be used by default.

If you do not want Sketchpacks to generate your appcast feed, you can define a
custom appcast feed, using an `appcast.xml` file in your repository.

### Custom Appcast Feed

1. ensure your repository has an `appcast.xml` file present
2. set the `appcast_path` property in your [plugin's settings file](./settings.md)
3. commit your changes to the repository

> **Note**: You will need to include the Sketchpacks plugin update endpoint
manually if you want to take advantage of the user updating insights.

### Push Workflow

When you push to your default branch, Sketchpacks will sync with the repository.
To update your appcast, bump your plugin version and push the changes to your
default branch.

You can use the `npm` versioning command:
```
npm version <new-version>
```

Or the `skpm` publish command:
```
skpm publish <new-version> --skip-release
```

However, you will only ever have one `HEAD` release in your appcast.  If you need
to support multiple versions for older Sketch clients, you will need to use the `release`
workflow instead.

> Note: Release notes are not available using the push workflow

Here is an example appcast from the plugin [PDF export](https://sketchpacks.com/DWilliames/PDF-export-sketch-plugin),
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
automatically be added to your appcast feed.

We recommend that you [use SKPM to publish your releases](https://github.com/skpm/skpm#publish-the-plugin-on-the-registry).
It simplifies building, versioning, and publishing your releases on GitHub.

```
skpm publish <new-version>
```

The release workflow is great for when you need to retain older versions for users
on old Sketch clients.  Also, it provides you with the ability to add change logs
to your appcast feed.

Here is an example appcast for the plugin [Keys For Sketch](https://sketchpacks.com/exevil/Keys-For-Sketch),
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

    ... omitted for brevity ...

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

#### Removing releases from your appcast

To remove a release from your appcast you need to delete the release from github. The
new state will be synced with Sketchpacks and the releases will be removed from
your appcast feed.

### Next Steps

* [Include change logs in your releases](./releases.md)
* [Add status badges to your readme](./badges.md)
* [Monitor your plugins activity](./../analytics.md)

---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/appcast.md).
