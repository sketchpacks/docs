# Sketchpacks Relay - Settings

## Setup

- Create a `.sketchpacks.json` settings file in your repositories root directory
- Use the `Sketchpacks Relay - Core Settings Schema 1.0.0` to define your settings

**Important**: the `schema_version` and `manifest_path` properties must be present!

```json
{
  "schema_version": "1.0.0",
  "manifest_path": "path/to/your/manifest.json",
  "appcast_path": "path/to/your/appcast.xml"
}
```

## Core Settings Schema 1.0.0

```json
{
  "$schema": "http://json-schema.org/draft-06/schema#",
  "title": "Sketchpacks Relay - Core Settings Schema 1.0.0",
  "type": "object",
  "required": ["schema_version", "manifest_path"],
  "properties": {
    "schema_version": {
      "description": "The schema version being used to define your settings",
      "type": "string",
      "pattern": "1.0.0"
    },
    "appcast_path": {
      "description": "the file path to your repositories appcast.xml",
      "type": "string",
      "default": ".appcast.xml",
      "minLength": 1
    },
    "manifest_path": {
      "description": "the file path to your repositories manifest.json",
      "type": "string",
      "default": "src/manifest.json",
      "minLength": 1
    }
  }
}
```

### Next Steps

* [Learn more about managing your appcast feed](./appcast.md)


---

###### Caught a mistake or what to contribute to the documentation? [Edit this page on Github](https://github.com/sketchpacks/docs/blob/master/developers/publishing/settings.md).
