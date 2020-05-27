[![license](https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow?style=flat)](https://creativecommons.org/licenses/by-sa/4.0/)
![GitHub repo size](https://img.shields.io/github/repo-size/salestim/template-manifests)
![semver](https://img.shields.io/badge/semver-2.0.0-green?style=flat)
![GitHub last commit](https://img.shields.io/github/last-commit/salestim/template-manifests)
![GitHub Release Date](https://img.shields.io/github/release-date/salestim/template-manifests)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/salestim/template-manifests)
[![linkedin](https://img.shields.io/badge/follow-@salestim-blue?logo=linkedin&logoColor=white)](https://www.linkedin.com/company/salestim/)
[![twitter](https://img.shields.io/badge/follow-@salestim-blue?logo=twitter&logoColor=white)](https://twitter.com/intent/follow?screen_name=salestimcrm)
[![store](https://img.shields.io/badge/visit-SalesTim%20Template%20Store-black?logo=microsoft-teams&logoColor=white)](https://store.salestim.com)

*"SalesTim Template Manifests" is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).*

# Welcome to the the Microsoft Teams® Template Manifests repo

## ABSTRACT

This repository contains manifests defining characteristics of the templates published on the ***[SalesTim Template Store](https://store.salestim.com)***.  
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
- **[X. APPENDICES](#x-appendices)**
  - COMMUNICATING WITH THE TEAM
  - SECURITY POLICY
  - CODE OF CONDUCT

## A. INTRODUCTION TO TEMPLATE MANIFESTS

Template manifests are plain [JSON Files](https://en.wikipedia.org/wiki/JSON), which is an open standard file format that guarantees portability.

To validate their structure, we're using a [JSON schema](https://en.wikipedia.org/wiki/JSON#JSON_Schema). Our JSON schema adheres to the [JSON Schema Draft 4](https://json-schema.org/draft-04/json-schema-core.html) specification.

To learn more about our template schema, including all fields, options and rules, please refer to our [Template Manifests JSON Schema](https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json).

## B. CREATE YOUR OWN TEMPLATE MANIFEST

### 1. Get the Sources

```console
# Clone this repo
git clone https://github.com/SalesTim/template-manifests.git
```

### 2. Create your Manifest

**Option 1: Using SalesTim**

1. Open your [SalesTim Template Catalog](https://app.salestim.io/forms?stEntityId=io.salestim.automation.catalog)
2. Create a new template from an existing team (or create a new team for that purpose)
3. Open the newly created template and click `Export...`
3. Save your `*.json` file to the following folder `manifests / <publisher> / <template>.json`

**Option 2: Using an existing template**  

Just copy an existing manifest and paste it in the following folder: `manifests / <publisher> / <template>.json`

### 3. Test your Manifest

**Option 1: Using SalesTim**

Once your manifest has been created:
1. Open your [SalesTim Template Catalog](https://app.salestim.io/forms?stEntityId=io.salestim.automation.catalog)
2. Click `Import a template...`
3. Select your `*.json` file

If any error occurs during the import process, including an incorrect manifest schema, the detailed error will be displayed.

**Option 2: Using Visual Studio Code**

Full Intellisense, inline documentation and schema validation during manifest authoring in Visual Studio Code is supported as long as your manifest starts with the following line:
```yaml
{
  "$schema": "https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json"
}
```

## C. PUBLISH YOUR TEMPLATE MANIFEST

### Submission process

With the manifest verified, you will need to submit a PR. 

Your manifest must be located in the folder path matching:
```sh
.
├── manifests
│   └── <publisher>          # The name of the organization that publishes the template. For example: "contoso".
│       ├── <template>.json  # The template name. For example: "a-great-template.json".
```


**Naming conventions**
- Avoid creating multiple publisher folders. For example, do not create "contoso-ltd." if there is already a "contonso" folder.
- Folders and files names should be lower-cased
- Supported characters:
  - Folders and files should use alphanumerics characters only.
  - As an exception, you can use "`-`" to replace spaces
  - As an exception, you can use "`.`" for versions numbers or dot notation.
- Versionning:
  - You souldn't use version numbers in file names to avoid redundency as the manifest's version number is already included as a field in the json file
  - As an exception, create multiple versions of the same template only if you want to keep these versions live at the same time on the store website.

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

```yaml
{
  "$schema": "https://dist.salestim.com/api/v1.0/json-schemas/io.salestim.automation.templates.schema.json",
  "manifestVersion": "1.0",
  "publisher": {
    "name": "Contoso Ltd",
    "description": "Microsoft Teams templates creator",
    "id": "com.contoso",
    "logo": "https://www.contoso.com/logo.png",
    "websiteUrl": "https://www.consoto.com",
    "privacyUrl": "https://www.consoto.com/privacy",
    "termsOfUseUrl": "https://www.consoto.com/tos"
  },
  "templateConfiguration": {
    "id": "com.contoso.a-great-template",
    "language": "en-us",
    "enabled": "true",
    "version": "1.0",
    "name": "A Great Template",
    "description": "A fantastic template to do crazy stuffs",
    "pictureUrl": "https://source.unsplash.com/random/80x80",
    "cardPicture": "https://source.unsplash.com/random/400x300",
    "screenshots": [
      "https://source.unsplash.com/random/800x600"
    ],
    "categories": [
      "productivity"
    ]
  },
  "initialization": {
    "structure": {
      "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
      "visibility": "Private",
      "displayName": "🔥 GREAT-TEMPLATE",
      "description": "DO NOT DELETE: Source team for the 'A Great Template'.,
      "channels": []
    }
  }
}
```

### Best Practices

- Each field in the file must be [camelCased](https://en.wikipedia.org/wiki/Camel_case) and cannot be duplicated.
- As a publisher id, we recommend to use a [Reverse Domain Name Notation](https://en.wikipedia.org/wiki/Reverse_domain_name_notation) such as "`com.contoso`"
- How to generate a unique template ID?
  - Option 1: Generate manually a unique but descriptive template id by combining:
    - Your publisher id
    - The template name (lower-cased and without spaces)
    - Example: `com.contoso.a-great-template`
  - Do not use language or version number to avoid redundencies
- Provide as many fields as possible. The more data you provide the better the user will find the template.

### Compatibility with Microsoft Teams Standard Templates

The manifest section that defines the contents and apps to be provisionned during the template initialization (Field: `> initialization -> structure`) is fully compliant with the [Microsoft Teams templates schema](https://docs.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates), and supports all the standard properties:
```yaml
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

## X. APPENDICES

### COMMUNICATING WITH THE TEAM

The easiest way to communicate with the team is via [GitHub Issues](https://github.com/SalesTim/template-manifests/issues/).

Please [file new issues](https://github.com/SalesTim/template-manifests/issues/new/choose), feature requests and suggestions, but **DO search for similar open/closed pre-existing issues before creating a new issue.**

If you would like to ask a question that you feel doesn't warrant an issue (yet), please reach out to us via Twitter:

- Guillaume Meyer: [@guillaumemeyer](https://twitter.com/guillaumemeyer)
- Alexandre Cipriani: [@alcip](https://twitter.com/alcip)

### SECURITY POLICY

This project has adopted the [SalesTim Security Policy](https://developers.salestim.com/platform/securitypolicy.html).

### CODE OF CONDUCT

This project has adopted the [SalesTim Open Source Code of Conduct](https://codeofconduct.salestim.com).

Resources:
- [SalesTim Open Source Code of Conduct](https://codeofconduct.salestim.com/)
- [SalesTim Code of Conduct FAQ](https://codeofconduct.salestim.com/faq/)
- Contact [codeofconduct@salestim.com](mailto:codeofconduct@salestim.com) with questions or concerns
