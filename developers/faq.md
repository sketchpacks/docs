# Developer Frequently Asked Questions

### I installed Sketchpacks Relay but can not see my plugin

First, make sure your plugin meets the [essential requirements](./publishing/essentials.md)
for Sketchpacks. If so, it could be a parse error in your `manifest.json` or `package.json` files.
Be sure to lint your JSON files before committing changes.

If the problem persists, please reach out to us and we'll investigate further.

### Why is my plugins usage activity unavailable?

You must use the [Sketchpacks Appcast feed](./publishing/appcast.md) to enable these metrics.

### How does Sketchpacks build my appcast feed?

Sketchpacks uses two workflows to build appcasts, the `push` and `release` workflows.
If the plugin repository contains releases, then the `release` workflow will be used.
Otherwise, the `push` workflow will be used by default.

See the section on [publishing appcasts](./publishing/appcast.md) for more information.
