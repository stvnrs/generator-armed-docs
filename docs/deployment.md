# Sub-generator: deployment

A _deployment_ is a set of related set of resources that are deployed to the same resource group.  There may be a 1-2-1 or many-2-1 relational deployments and resource groups in your solution.

## Adding a deployment

A deployment is added to your solution by running the _deployment_ sub-generator.

```pwsh
yo armed:deployment
```

You will be prompted to enter a name for the deployment, or you can accept the default _core_ by pressing return.

![example](./create-deployment.gif)

This will create a folder in the solution's deployments folder with the name you entered at the prompt which contains the following files.

```text
deployments
└─singe
    _deployment.json
    functions.json
    outputs.json
    resources.json
    variables.json
    _parameters.json
```

The purpose of each of these files is explained below:

### _deployment.json

  The __deployment.json_ file defines the schema, contentVersion and parameters for the ARM template. 

  **Note**: the content version does not need to be maintained as it will be automatically updated when the solution is built to match the version number of the solution.

  ```json
  {
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
      }
    }
  }
  ```

#### Example

This example contains a single parameter _deploymentRing_, which can be one of a set of allowed values.

```json
:(../samples/sub-generators/deployment/deployments/singe/_deployment.json)
```

### functions.json

The __functions.json_ file contains custom functions used in the arm template. A deployment can have multiple function files e.g. by namespace. These should be named \_functions.{id}.json e.g. \_functions.ns1.json, \_functions.ns2.json.

```json
{
  "functions": [

  ]
}
```

#### Example

This example shows a function that calculates an identifer for a resource based on its type and location.

```json
:(../samples/sub-generators/deployment/deployments/singe/functions.json)
```

### variables.json

The __variables.json_ file contains variables functions used in the arm template. A deployment can have multiple variables files. These should be named \_variables.{id}.json e.g. \_variables.a.json, \_variables.b.json.

```json
{
  "variables": {
  }
}
```

#### Example

This example shows...

```json
:(../samples/sub-generators/deployment/deployments/singe/variables.json)
```

### resources.json

The __resources.json_ file contains resources deployed by the arm template. A deployment can have multiple resources files. These should be named \_resources.{id}.json e.g. \_resources.a.json, \_resources.b.json.

```json
{
  "resources": [
  ]
}
```

#### Example

```json
:(../samples/sub-generators/deployment/deployments/singe/resources.json)
```

### outputs.json

The __outputs.json_ file contains outputs deployed by the arm template. A deployment can have multiple outputs files. These should be named \_outputs.{id}.json e.g. \_outputs.a.json, \_outputs.b.json.

```json
{
  "outputs": {
  }
}
```

#### Example

```json
:(../samples/sub-generators/deployment/deployments/singe/outputs.json)
```

### _parameters.json

The __parameters.json_ file contains the deployment parameters i.e. the parameter values used at deployment time.  A deployment can have multiple deployment parameters e.g. to deal with different deployment rings. These should be named \_parameters.{id}.json e.g. \_parameters.dev.json, \_parameters.test.json etc.

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentParameters.json#",
    "parameters": {
    }
}
```

#### Example

```json
:(../samples/sub-generators/deployment/deployments/singe/_parameters.json)}
```

## Build

Build all deployments in the solution:

```bash
gulp build:deployments
```

Build a specific deployment:

```bash
gulp deployment:{{deployment name}}
```

e.g.

```bash
gulp deployment:singe
```

The build process for a deployment:

- assembles all the template fragments, including functions and variables from the _common deployment - if one exists for the solution.

- writes the assembled template to `build\{{deployment-name}}`.

- copies any parameter files to `build\{{deployment-name}}`.

- updates the content version in output files to match the version number in `package.json`.

- prettifies all output files.

### Built parameter file

```json
:(../samples/sub-generators/deployment/build/singe/singe.parameters.json)}
```

### Built deployment template

<iframe width=100% src="https://www.youtube-nocookie.com/embed/rY39IL-Sd94" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

```json
:(../samples/sub-generators/deployment/build/singe/singe.deployment.json)}
```