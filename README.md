[![license](https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow?style=flat)](https://creativecommons.org/licenses/by-sa/4.0/)&nbsp;
![version](https://img.shields.io/badge/version-1.0.0-green?style=flat)&nbsp;![semver](https://img.shields.io/badge/semver-2.0.0-green?style=flat)&nbsp;[![linkedin](https://img.shields.io/badge/follow-@salestim-blue?logo=linkedin&logoColor=white)](https://www.linkedin.com/company/salestim/)&nbsp;[![twitter](https://img.shields.io/badge/follow-@salestim-blue?logo=twitter&logoColor=white)](https://twitter.com/intent/follow?screen_name=salestimcrm)&nbsp;[![store](https://img.shields.io/badge/visit-SalesTim%20Template%20Store-black?logo=microsoft-teams&logoColor=white)](https://store.salestim.com)

*"SalesTim Template Manifests" is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).*

# Welcome to the SalesTim Community Microsoft Teams Template Manifests repo

## ABSTRACT

This repository contains manifests defining the templates published on the ***[SalesTim Template Store](https://store.salestim.com)***.  
A manifest is a simple file that describes the properties of a Microsoft Teams template with respect to the Microsoft Teams and the SalesTim platforms, especially:
- **Contents and apps to be provisioned**
- **Naming conventions & tagging**
- **Approval workflow**
- **Security and compliance policies**
- **Lifecycle policies**

To learn more about SalesTim templates capabilities, including how to create templates visually from our UI, please refer to our ***[Help Center](https://help.salestim.com/)***.

If you want to integrate your contents or applications with the SalesTim Platform API, for instance create template-based teams from Microsoft PowerAutomate, please refer to our ***[Tech Hub](https://developers.salestim.com/)***.

## TABLE OF CONTENTS

- **[A. INTRODUCTION TO TEMPLATE MANIFESTS](#a-introduction-to-template-manifests)**
- **[B. CREATE YOUR OWN TEMPLATE MANIFEST](#b-create-your-own-template-manifest)**
  1. Get the Sources
  2. Create your Manifest
  3. Test your Manifest
- **[C. PUBLISH YOUR TEMPLATE MANIFEST](#c-publish-your-template-manifest)**
  - Submission Process
  - Validation Process
  - Respond to Feedback
- **[D. TEMPLATE MANIFESTS SPEC](#d-template-manifests-spec)**
  - Minimal JSON File Example
  - Best Practices
  - Compatibility with Microsoft Teams Standard Templates
- **[E. USEFUL LINKS](#e-useful-links)**

## A. INTRODUCTION TO TEMPLATE MANIFESTS

Template manifests are plain [JSON Files](https://en.wikipedia.org/wiki/JSON), which is an open standard file format that guarantees portability.

To validate their structure, we're using a [JSON schema](https://en.wikipedia.org/wiki/JSON#JSON_Schema). Our JSON schema adheres to the [JSON Schema Draft 4](https://json-schema.org/draft-04/json-schema-core.html) specification.

To learn more about our template schema, including all fields, options and rules, please refer to our [Template Manifests JSON Schema](https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json).

## B. CREATE YOUR OWN TEMPLATE MANIFEST

### 1. Get the Sources

``` sh
# Clone this repo
git clone https://github.com/SalesTim/template-manifests.git
```

### 2. Create your Manifest

**Option 1: Using SalesTim**

1. Open your [SalesTim Template Catalog](https://app.salestim.io/forms?stEntityId=io.salestim.automation.catalog)
2. Create a new template from an existing team (or create a new team for that purpose)
3. Open the newly created template and click `Export...`
3. Save your `*.json` file to the following folder `manifests / <publisher> / <template>`

**Option 2: Using an existing template**  

Just copy an existing manifest and paste it in the following folder: `manifests / <publisher> / <template>`

### 3. Test your Manifest

**Option 1: Using SalesTim**

Once your manifest has been created:
1. Open your [SalesTim Template Catalog](https://app.salestim.io/forms?stEntityId=io.salestim.automation.catalog)
2. Click `Import a template...`
3. Select your `*.json` file

If any error occurs during the import process, including an incorrect manifest schema, the detailed error will be displayed.

**Option 2: Using Visual Studio Code**

Full Intellisense, inline documentation and schema validation during manifest authoring in Visual Studio Code is supported as long as your manifest starts with the following line:
``` json
{
  "$schema": "https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json"
}
```

## C. PUBLISH YOUR TEMPLATE MANIFEST

### Submission process

With the manifest verified, you will need to submit a PR. 

Your manifest should be located in the folder path matching:
```
/ manifests / <publisher> / <template> / <version>.json
```

-  `<publisher>` folder is the name of the organization that publishes the template. For example: ***SalesTim***.
-  The child folder `<template>` is the name of the template. For example: ***Crisis Management***.
-  The filename must be the current `<version>` following the [Semantic Versioning Specification (SemVer)](https://semver.org/), prefixed with the "`v`" character. For example: ***v1.0.0.json***.

### Validation Process

The PR request will go through a validation process.
- During the process, the PR request will get labels to help drive the validation. 
- Manifests are validated against our [Template Manifests JSON Schema](https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json) and will be automatically rejected until rectified.
- In the event of a failure, we'll include comments and assign the PR back to you.

### Respond to Feedback

If the PR has been assigned to you, a timer is triggered. You will have 7 days to resolve the issue, or the PR will be closed.

## D. TEMPLATE MANIFESTS SPEC

### Minimal JSON File Example
As specified in our [Template Manifests JSON Schema](https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json), only a number of fields are required as we're applying a number of default values. The minimal supported JSON file would look like this:

``` json
{
  "$schema": "https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json",
  "manifestVersion": "1.0",
  "publisher": {
    "name": "SalesTim",
    "description": "Microsoft Teams Governance Automation Platform",
    "id": "io.salestim",
    "logo": "https://store.salestim.com/color.png",
    "websiteUrl": "https://www.salestim.com",
    "privacyUrl": "https://www.salestim.com/legal/privacy",
    "termsOfUseUrl": "https://www.salestim.com/legal/tos"
  },
  "templateConfiguration": {
    "id": "io.salestim.automation.templates.dealRoom.en-us",
    "language": "en-us",
    "enabled": "true",
    "version": "1.0",
    "name": "Deal Room",
    "description": "A basic team comprised of one 'General' channel",
    "pictureUrl": "https://source.unsplash.com/random/80x80",
    "cardPicture": "https://source.unsplash.com/random/400x300",
    "screenshots": [
      "https://source.unsplash.com/random/800x600"
    ],
    "categories": [
      "io.salestim.gallery.categories.productivity"
    ]
  },
  "initialization": {
    "structure": {
      "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
      "visibility": "Private",
      "displayName": "TEMPLATE_NAME",
      "description": "TEMPLATE_NAME",
      "channels": [
        {
          
        }
      ]
    },
    "contents": {}
  }
}
```

### Best Practices

- Each field in the file must be [camelCased](https://en.wikipedia.org/wiki/Camel_case) and cannot be duplicated.
- The Id must be unique. You cannot have multiple submissions with the same Id.
- Avoid creating multiple publisher folders. For example, do not create "Contoso Ltd." if there is already a "Contonso" folder.
- Provide as many fields as possible. The more data you provide the better the user will find the template.
- Length of strings in this spec should be limited to 100 characters before a line break.

### Compatibility with Microsoft Teams Standard Templates

The manifest section that defines the contents and apps to be provisionned during the template initialization (Field: `> initialization -> structure`) is fully compliant with the [Microsoft Teams templates schema](https://docs.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates), and supports all the standard properties:
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

## E. USEFUL LINKS
- [Report an issue](https://github.com/SalesTim/template-manifests/issues/new/choose)
- [Security Policy](https://github.com/SalesTim/template-manifests/blob/master/SECURITY.md)
