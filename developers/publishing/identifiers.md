# Unique Plugin Identifiers

Sketch as well as Sketchpacks needs a unique identifier to track your plugin. You
can define your plugin's `identifier` in the `manifest.json` or `package.json` file.

From the Sketch developer documentation: http://developer.sketchapp.com/guides/plugin-bundles/#manifest

> **Identifier**
> A string specifying a unique identifier for the Plugin.
> Reverse-domain syntax is strongly encouraged, for example com.example.sketch.shape-plugins.
> Sketch uses this string internally to track the Plugin, store settings for it, etc.

## Requirements

* you must provide a unique plugin identifier
* you must provide a identifier with only alpha-numeric characters, "-", "\_", and periods
* you must define the `identifier` property in the `manifest.json`
* you may define the `identifier` property in the `package.json`

> **Warning**: You can not migrate your plugin identifiers at this time.  We are working
on a solution for this, and will deploy it ASAP!

### Setup Examples

Example `manifest.json`:

```json
{
  "name" : "My Awesome Plugin",
  "identifier" : "my.awesome.plugin",
  "appcast": "https://api.sketchpacks.com/v1/plugins/my.awesome.plugin/appcast"
}
```

Example `skpm` settings in the `package.json`:

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

Sketchpacks will check for plugin identifiers using the following order:

1. manifest identifier
2. package skpm identifier

**If an identifier can not be found, the plugin will not be inserted into the registry.**

### Using identifiers in the Sketchpacks API

Plugin identifiers can be used as a primary key to fetch a plugin from the Sketchpacks API.
So, for example, if your plugin identifier was named: `com.sketchpacks.awesome-plugin`,
then the API endpoint would be:

```
https://api.sketchpacks.com/v1/plugins/com.sketchpacks.awesome-plugin
```

You can also use this identifier to fetch additional plugin information, such as your
manifest, releases, or appcast feed.

```
https://api.sketchpacks.com/v1/plugins/com.sketchpacks.awesome-plugin/appcast
https://api.sketchpacks.com/v1/plugins/com.sketchpacks.awesome-plugin/manifest
https://api.sketchpacks.com/v1/plugins/com.sketchpacks.awesome-plugin/readme
https://api.sketchpacks.com/v1/plugins/com.sketchpacks.awesome-plugin/versions
```

See the [Sketchpacks API Reference](http://docs.sketchpacks.apiary.io) for more information.

### Using identifiers in Sketchpacks plugin bundles

When a plugin bundle is exported, Sketchpacks will use your plugins identifier as
the primary key to reference your plugin in the bundle.  When a plugin bundle is
being imported, Sketchpacks will also use the plugin identifier to lookup the plugin
in the registry.

### Next Steps

* [Configure your plugins manifest path](./settings.md)
