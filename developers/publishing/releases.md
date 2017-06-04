# Releases

[Software versioning](https://en.wikipedia.org/wiki/Software_versioning) is the basic foundation
for allowing developers to create reference-able milestones of any point within their code's revision history.

Sketchpacks works by serving your [published releases](https://help.github.com/articles/creating-releases/) from Github which have attached release assets containing your [Sketch plugin bundle](http://developer.sketchapp.com/introduction/plugin-bundles/).

> **Note**: Only `.zip` files are supported as enclosures.

The Sketchpacks Appcast API endpoint serves your feed enumerating your published releases on Github.

As of Sketch 45, native plugin updating is available based on
the [Sparkle](https://sparkle-project.org/) software update framework available which may consume your [Appcast feed](./appcast.md).
