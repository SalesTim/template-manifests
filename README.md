[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

*"SalesTim Template Manifests" is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).*

# Welcome to the SalesTim community Microsoft Teams Template manifests repo

This repository contains manifests defining the templates published on the [SalesTim Template Store](https://store.salestim.com).

## Abstract

A manifest is a simple text file that describes the properties of a Microsoft Teams template with respect to the Microsoft Teams and SalesTim platforms, especially:
- Contents and apps to be provisioned
- Naming conventions & tagging
- Approval workflow
- Security and compliance policies
- Lifecycle policies

To learn more about SalesTim templates capabilities, including how to create templates visually from our UI, please refer to our [Help Center](https://help.salestim.com/).

If you want to integrate your application with the SalesTim Platform API, for instance create template-based teams from Microsoft PowerAutomate, please refer to our [Tech Hub](https://developers.salestim.com/).

## Template manifests

Template manifests are plain [JSON files](https://en.wikipedia.org/wiki/JSON).  
To control their structure, we're using a [JSON schema](https://en.wikipedia.org/wiki/JSON#JSON_Schema). Our JSON schema adheres to the [JSON Schema Draft 4](https://json-schema.org/draft-04/json-schema-core.html) specification.

To learn more about our template schema, including all properties, options and rules, please refer to our [JSON Template Schema](https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json).

N.B: The manifest section that defines the contents and apps to be provisionned during the template initialization (`> initialization -> structure`) is fully compliant with the [Microsoft Teams templates schema](https://docs.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates), and supports these standard properties:
``` json
{
  "channels": {},
  "memberSettings": {},
  "guestSettings": {},
  "funSettings": {},
  "messagingSettings": {},
  "discoverySettings": {},
  "installedApps": {}
}
```

## Contribute

### 1. Get the sources and build

``` sh
# Clone this repo
git clone https://github.com/SalesTim/template-manifests.git
```

### 2. Create your manifest

**Option 1: Using SalesTim**

1. Open your [SalesTim Template Catalog](https://app.salestim.io/forms?stEntityId=io.salestim.automation.catalog)
2. Create a new template from an existing team (or create a new team for that purpose)
3. Open the newly created template and click `Export...`
3. Save your `*.json` file to the following folder `manifests / <publisher> / <template>`

**Option 2: Using an existing template**  

Just copy an existing manifest and paste it in the following folder: `manifests / <publisher> / <template>`

### 3. Test your manifest

**Option 1: Using SalesTim**

Once your manifest has been created:
1. Open your [SalesTim Template Catalog](https://app.salestim.io/forms?stEntityId=io.salestim.automation.catalog)
2. Click `Import a template...`
3. Select your `*.json` file

If any error occurs during the import process, including an incorrect manifest schema, the detailed error will be displayed.

**Option 2: Using Visual Studio Code**

Full Intellisense, inline documentation and schema validation during manifest authoring in Visual Studio Code is supported as long as your manifest starts with the following line:
```json
{
  "$schema": "https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json"
}
```

## Submit your manifest

With the manifest verified, you will need to submit a PR. Your manifest should be located in the folder path matching:
``` bash
manifests / <publisher> / <template> / <version>.json
```

*⚠ Manifests are validated against our [JSON Template Schema](https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json) during publishing and will be automatically rejected until rectified.*

### Validation Process

The PR request will go through a validation process. During the process, the PR request will get labels to help drive the validation. In the event of a failure, we'll include comments and assign the PR back to you.

### Respond to feedback

If the PR has been assigned to you, a timer is triggered. You will have 7 days to resolve the issue, or the PR will be closed.

## Useful Links
- [Report an issue](https://github.com/SalesTim/template-manifests/issues/new/choose)
- [Security Policy](https://github.com/SalesTim/template-manifests/blob/master/SECURITY.md)
