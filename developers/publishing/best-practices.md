# Best Practices for Publishing Plugins

Now that your plugins have met the minimum requirements, let’s go over some ways
to increase their exposure on the registry.

### Use SKPM to publish releases

SKPM simplifies the process of building, packaging, and publishing your plugin.
It also automates the tasks of bumping your plugin version and creating github
releases. Combined with Sketchpacks, you can quickly build and distribute updates
for your users!

Publishing a release is as simple as:

```
skpm publish <new-version>
```

For more information, see our section on [publishing plugin updates](./developers/publishing/providing-plugin-updates.md)

### Have a detailed readme tutorial

We high recommend taking the time to create a concise, yet informative
readme for your users. Sketchpacks syncs your readme and renders it on your plugins
page. Having a brief tutorial on your readme can greatly help users understand your
plugins features.

Quick, informational gifs are very useful for showing off what your plugin can do
and catching the eyes of window shoppers. It also gives you a place to link users
to more detailed documentation and tutorials for your plugin.

### Have a detailed manifest for your plugin

The more metadata you can add to your manifest, the better Sketchpacks will be
able to categorize and display it.

### Have a detailed package for your plugin

Not only is the `package.json` a great place for versioning your plugin, it also
another great source of metadata. Sketchpacks will sync with your repositories
`package.json` and use it for any required information that may be missing from your
plugins `manifest.json`.

### Next Steps

* [Choose a plugin identifier](./identifiers.md)
* [Provide plugin updates](./providing-plugin-updates.md)
* [Automate your appcast feed](./appcast.md)
* [Include change logs in your releases](./releases.md)
* [Add status badges to your readme](./badges.md)

---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/best-practices.md).
