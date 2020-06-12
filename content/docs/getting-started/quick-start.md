---
title: "Quick Start"
linkTitle: "Quick Start"
---

## Pre-requisites

- Install/update PowerShell [Az](https://docs.microsoft.com/en-us/powershell/azure/install-az-ps?view=azps-3.8.0) or the [azure-cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest).

- Install/update *node* & *npm* for your platform [nodejs.org](https://nodejs.org/en/).

- Install *gulp* globally - global install is required for VS Code to detect gulp build tasks.

  ```Powershell
  npm install --global gulp
  ```

- Install *yeoman* - see yeoman's [docs](https://yeoman.io/learning/index.html) for a detailed walkthrough.

  ```Powershell
  npm install --global yo
  ```

- Install *armed* from the npm repository

  ```Powershell
  npm install --global generator-armed
  ```

## Creating an armed solution

- Open your favorite terminal and create a new folder for your project:

  ```pwsh
  mkdir my-armed-project
  cd my-armed-project
  ```

- Run _npm init_ to initialize your project. See npm's [docs](https://docs.npmjs.com/) for a more detailed walkthrough of this process.

  ```pwsh
  npm init
  ```

  which will give output similar to:

  ```text
  This utility will walk you through creating a package.json file.
  It only covers the most common items, and tries to guess sensible defaults.

  See `npm help json` for definitive documentation on these fields
  and exactly what they do.

  Use `npm install <pkg>` afterwards to install a package and
  save it as a dependency in the package.json file.

  Press ^C at any time to quit.
  package name: (my-armed-project)
  version: (1.0.0)
  description: Super cool armed project!
  entry point: (index.js)
  test command:
  git repository:
  keywords: arm
  author: Ricky Swift
  license: (ISC)
  About to write to C:\Users\StevenRose\source\repos\my-armed-project\package.json:
  {
    "name": "my-armed-project",
    "version": "1.0.0",
    "description": "Super cool armed project!",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [
      "arm"
    ],
    "author": "Ricky Swift",
    "license": "ISC"
  }


  Is this OK? (yes)
  ```

- Install *gulp* packages required for building your armed solution.

  ```bash
  npm install gulp gulp-clean gulp-bump gulp-jsbeautify gulp-merge-json gulp-replace --save-dev
  ```

- Run the *armed* generator:
Armed will prompt you for any required inputs - you can accept the defaults by pressing return or enter your own values.

  ```Powershell
  yo armed
  ```

  which will give output similar to:

  ```text
  ? Your project name my-armed-project
  ? Add tenant deployment true
  ? Add subscription deployment true
  ? Add group deployment true
  ? Name of group deployment core
    create .gitignore
    create .vscode\snippets.code-snippets
    create gulpfile.js
    create deployments\tenant\tenant-deployment.json
    create deployments\subscription\subscription-deployment.json
    create deployments\core\_deployment.json
    create deployments\core\_parameters.json
    create deployments\core\resources.json
    create deployments\core\variables.json
    create deployments\core\functions.json
    create deployments\core\outputs.json
  ```

## Output

This will create a folder structure like this:

```Powershell
.
├───.vscode
└───deployments
    ├───_common
    ├───core
    ├───subscription
    └───tenant
```

### .vscode

Contains vscode config files including solution specific settings, snippets etc.

### deployments/_common

This folder contains files that will be included with all deployments. By default it contains 2 files:

```Powershell
    functions.json
    variables.json
```

- functions.json should contain any functions that need to be consistent across all deployments e.g. functions used to generate resource names.
- variables.json should contain variables that need to be consistent across all deployments.

### deployments/core

```text
    _deployment.json
    _parameters.json
    functions.json
    variables.json
    resources.json
    outputs.json
```

### Files

#### _deployment.json

File name can be overridden in .yo-rc.json (not yet supported)

This file contains ...

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "",
    "apiProfile": "",
    "parameters": {  }
  }
```

Note: only schema and parameter objects are required. Parameters can be empty.

Example:

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0",
    "parameters": {  

    }
  }
```

#### _parameters.json

```json
{
    "parameters": {  }
}
```

Example:

```json
{
    "parameters": {  }
}
```
