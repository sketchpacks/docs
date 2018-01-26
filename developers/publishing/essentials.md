# Essentials for Publishing Plugins

To publish plugins on Sketchpacks, your repository and plugin metadata must meet
the following requirements.

### Repository Requirements

At it's most basic level, Sketchpacks syncs with git repositories.  If Sketchpacks
can not connect with a repository, the plugin will not be available in the registry.

* Repositories must contain a [manifest.json file](http://developer.sketchapp.com/guides/plugin-bundles/#manifest).
* Repositories may contain a [package.json file](https://github.com/skpm/skpm/blob/master/template/package.json). (optional)

These basic requirements help keep the registry free of repositories that are not
Sketch plugins.  It also helps us ensure that all plugins in the registry meet the
same basic structure.

### Plugin Requirements

* Plugins must have a [globally unique identifier](./identifiers.md)
* Plugins must have a valid [semantic version](http://semver.org/)
* Plugin Releases must have a valid [semantic version](http://semver.org/)

These basic requirements help ensure that all plugins in the registry are unique,
and can be accessed by their identifiers. It also ensures that plugin versions can be
correctly sorted using Semantic Versioning.

### Plugin Configuration on Sketchpacks

To configure your plugin, add a `.sketchpacks` directory to your repositories
root path. You can use this config directory to tell Sketchpacks where to find
your plugin's manifest and appcast files.

* The `.sketchpacks` directory must contain a `settings.json` file
* The `.sketchpacks/settings.json` file must use the [Sketchpacks Relay settings schema](./settings.md)

> **Important**: the `.sketchpacks` config directory is not required, but if Sketchpacks
can not find your manifest, or finds the wrong one, you will need to correct it here.

### Next Steps

* [Choose a plugin identifier](./identifiers.md)
* [Learn more about configuring your plugin](./settings.md)


---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/essentials.md).
