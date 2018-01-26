# Unique Plugin Identifiers

Plugin identifiers must meet the following requirements:

* Must be unique
* Must contain only alpha-numeric characters, "-", "\_", and periods.

> Tip: Use reverse-domain syntax for an easily unique identifier. ex: com.sketchpacks.awesome-plugin

> Warning: You can not migrate your plugin identifiers at this time.  We are working
on a solution for this, and will deploy it ASAP.

### Defining a plugin identifier

You can set the identifier for a plugin in the `manifest.json`

```json
{
  "identifier": "my.plugin.identifier"
}
```

Or, if you are using SKPM, you can set the identifier in the `skpm` property
in the `package.json`

```json
{
  "skpm": {
    "identifier": "my.plugin.identifier"
  }
}
```

Sketchpacks will check for identifiers using the following order:

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
