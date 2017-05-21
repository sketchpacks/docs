# Providing Plugin updates

With [Sketchpacks Relay]({{ book.relayURL }}) installed on your plugins' Github repos, providing updates is simple.

## Native Sketch plugin updates

The latest [Sketch beta](http://sketchplugins.com/d/229-updating-plugins) allows for plugin updates right from within Sketch itself. 👏🏽

Allowing your users to apply updates from within Sketch is done by simply adding a new property, `appcastURL`, to your `manifest.json` file.


```
// content omitted for brevity

{
  name: "Awesome Sketch Plugin",
  identifier: "com.sketchpacks.awesome-plugin",
  appcastURL: "https://api.sketchpacks.com/v1/plugins/com.sketchpacks.awesome-plugin/appcast"  
}
```
You may use the Appcast API Endpoint provided by the [Sketchpacks API]({{ book.apiDocsUrl }}) to serve your plugins' Appcast feed.

All your semantically versioned release assets published on Github will be available to all Appcast feed consumers.

[Try out the Appcast API endpoint](http://docs.sketchpacks.apiary.io/#reference/plugins/v1pluginsidentifierappcast/fetch-the-appcast-xml-for-a-plugins-releases)

## Auto-updates within Sketchpacks

If you have [Sketchpacks Relay]({{ book.relayURL }}) installed on your plugins' Github repos, then you're all set.

Sketchpacks will provide the users' desired level of updates by setting their lock strength to apply patch- and minor-level updates. Fully unlocked plugins will apply all updates.

### Resources

* Sketchpacks API - {{ book.apiDocsUrl }}