# Publishing Plugins with Sketchpacks Relay

Sketchpacks Relay is a Github Integration that connects your plugin repositories
to the registry. When you `push` or `release` changes to your plugin, Sketchpacks
will automatically deliver those updates to your users.

Sketchpacks Relay also helps provide better insights into your plugin's user
activity and retention!

## Getting Started

1. Ensure your plugin meets the [essentials for Sketchpacks](./publishing/essentials.md)
2. Create a [settings file](./publishing/settings.md) in your repository's root directory
3. Define a [unique identifier](./identifiers.md) for your plugin in the `manifest.json`
4. Install [Sketchpacks Relay]({{ book.relayURL }}) on your plugin repository
5. Done! Start building and publishing releases for your users!

## Next steps

* [Providing plugin updates](./publishing/providing-plugin-updates.md)
* [Publishing best practices](./publishing/best-practices.md)
* [Automate your appcast feed](./publishing/appcast.md)
* [Monitor your plugins activity](./analytics.md)
