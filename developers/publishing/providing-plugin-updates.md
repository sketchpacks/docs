# Providing Plugin Updates

With [Sketchpacks Relay]({{ book.relayURL }}) installed on your plugins' Github
repos, providing updates is simple. When you `push` or `release` changes to your
repository, Sketchpacks will automatically deliver those updates to your users.

## Managing your plugin updates

Sketchpacks supports two workflows for releasing your plugin's updates, the `push` and
`release` workflows. If your repository contains releases, Sketchpacks will use the
`release` workflow.  Otherwise the `push` workflow will be used by default.

### Push Workflow

When you `push` to your default branch, Sketchpacks will check if your plugins `version`
has changed. The new `version` will be updated in your plugin's `appcast` feed and
the next time your user's check for updates, it will be available to them.

We suggest that you use a command line tool to help with versioning your plugins.
For example, you can use `npm`:

```
npm version <new-version>
```

Or, you can use `skpm` to bump your plugin's `version`:

```
skpm publish <new-version> --skip-release
```

**Important** using this workflow, you will only ever have one `HEAD` release in
your appcast. If you need to support multiple Sketch versions, we suggest using the
release workflow.

### Release Workflow

When you create and publish new releases in your github repository, they will
automatically be added to your appcast feed. The next time your user's check for
updates, the new release will be available to them.

We recommend that you [use SKPM to publish your releases](https://github.com/skpm/skpm#publish-the-plugin-on-the-registry).
It simplifies building, versioning, and publishing your releases on GitHub.

```
skpm publish <new-version>
```

## Auto-updates within the Sketchpacks desktop client

Sketchpacks will provide the users' desired level of updates by setting their
lock strength to apply patch- and minor-level updates. Fully unlocked plugins
will apply all updates.

### Next Steps

* [Automate your appcast feed](./appcast.md)
* [Include change logs in your releases](./releases.md)
* [Add status badges to your readme](./badges.md)
* [Monitor your plugins activity](./../analytics.md)

---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/providing-plugin-updates.md).
