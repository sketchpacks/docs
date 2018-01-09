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
and can be accessed by their identifiers. It ensures that plugin versions can be
correctly sorted using Semantic Versioning.

### Next Steps

* [Publishing best practices](./best-practices.md)
* [Choose a plugin identifier](./identifiers.md)
* [Provide plugin updates](./providing-plugin-updates.md)
* [Automate your appcast feed](./appcast.md)
* [Include change logs in your releases](./releases.md)
* [Add status badges to your readme](./badges.md)
* [Monitor your plugins activity](./../analytics.md)


---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/essentials.md).
