# Publish Plugins with Sketchpacks Relay

## Setup your repository

- Ensure your plugin meets the [essentials for Sketchpacks](./publishing/essentials.md)
- Create a `.sketchpacks.json` settings file in your repositories root directory
- Define the path to your plugins `manifest.json` in the settings file
- Define the path to your plugins `appcast.xml` in the settings file. Or leave blank
to auto generate your plugins appcast with Sketchpacks.
- Add the Sketchpacks appcast API endpoint to your plugins `manifest.json`

## Connect your repository

- Install [Sketchpacks Relay]({{ book.relayURL }}) on your plugin repository to
keep it up-to-date in the registry

#### Example Settings File

Below is an example `.sketchpacks.json` file for your repository

```json
{
  "schema_version": "1.0.0",
  "manifest_path": "path/to/your/manifest.json",
  "appcast_path": "path/to/your/appcast.xml"
}
```

#### Example Plugin Manifest

Use the Sketchpacks appcast API endpoint for your plugin's appcast

```
https://api.sketchpacks.com/v1/plugins/:identifier/appcast
```

Use your plugin's [unique identifier](./publishing/identifiers.md) for the `:identifier` parameter

```json
{
  "name" : "My Awesome Plugin",
  "identifier" : "my.awesome.plugin",
  "appcast": "https://api.sketchpacks.com/v1/plugins/my.awesome.plugin/appcast"
}
```

If you are using `skpm` you can configure your plugin using the `package.json`

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

## Next steps

* [Automate your appcast feed](./publishing/appcast.md)
* [Monitor your plugins activity](./analytics.md)
