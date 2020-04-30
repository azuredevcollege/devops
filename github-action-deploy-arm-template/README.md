# GitHub Action for Azure Resource Manager (ARM) deployment
This example shows how you can use GitHub Actions to deploy an ARM template to Azure.

## What is an GitHub Action?
**GitHub describes this best itself:**   
GitHub Actions help you automate your software development workflows in the same place you store code and collaborate on pull requests and issues. You can write individual tasks, called actions, and combine them to create a custom workflow. Workflows are custom automated processes that you can set up in your repository to build, test, package, release, or deploy any code project on GitHub.

With GitHub Actions you can build end-to-end continuous integration (CI) and continuous deployment (CD) capabilities directly in your repository.

Source: https://help.github.com/en/actions/getting-started-with-github-actions/about-github-actions#about-github-actions

## How to use this Action
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec lorem urna, scelerisque at ultrices vel, semper vel mi. Aenean sagittis sagittis lectus, vitae commodo velit pharetra id. Maecenas sit amet viverra enim. Curabitur fermentum mi mollis augue hendrerit, vel efficitur dolor finibus. Maecenas ornare nunc sed lacus consequat, quis luctus elit tristique. Sed convallis sapien eget ex aliquet volutpat. Phasellus ante elit, accumsan eget lorem sit amet, tristique iaculis dui. Maecenas dignissim turpis velit, et eleifend purus dignissim ut.

### Required Inputs
* `creds` **Required** Paste output of `az ad sp create-for-rbac -o json` as value of secret variable: `AZURE_CREDENTIALS`  
(See [github-action-deploy-arm-template/assets/serviceprincipal.json](assets/serviceprincipal.json))

* `resourceGroupName` **Required** Provide the name of a resource group.

* `templateLocation` **Required** Specify the path to the Azure Resource Manager template.  
(See [github-action-deploy-arm-template/assets/serviceprincipal.json](assets/template.json))

* `deploymentMode` Incremental (only add resources to resource group) or Complete (remove extra resources from resource group). Default: `Incremental`.
  
* `deploymentName` Specifies the name of the resource group deployment to create.

* `parameters` Specify the path to the Azure Resource Manager parameters file.  
(See [github-action-deploy-arm-template/assets/serviceprincipal.json](assets/parameters.json))

## Usage
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec lorem urna, scelerisque at ultrices vel, semper vel mi. Aenean sagittis sagittis lectus, vitae commodo velit pharetra id. Maecenas sit amet viverra enim. Curabitur fermentum mi mollis augue hendrerit, vel efficitur dolor finibus. Maecenas ornare nunc sed lacus consequat, quis luctus elit tristique. Sed convallis sapien eget ex aliquet volutpat. Phasellus ante elit, accumsan eget lorem sit amet, tristique iaculis dui. Maecenas dignissim turpis velit, et eleifend purus dignissim ut.
```yaml
- uses: whiteducksoftware/azure-arm-action@v1
  with:
    creds: ${{ secrets.AZURE_CREDENTIALS }}
    resourceGroupName: <YourResourceGroup>
    templateLocation: <path/to/azuredeploy.json>
```

### Example Workflow
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec lorem urna, scelerisque at ultrices vel, semper vel mi. Aenean sagittis sagittis lectus, vitae commodo velit pharetra id. Maecenas sit amet viverra enim. Curabitur fermentum mi mollis augue hendrerit, vel efficitur dolor finibus. Maecenas ornare nunc sed lacus consequat, quis luctus elit tristique. Sed convallis sapien eget ex aliquet volutpat. Phasellus ante elit, accumsan eget lorem sit amet, tristique iaculis dui. Maecenas dignissim turpis velit, et eleifend purus dignissim ut.
```yaml
on: [push]
name: AzureLoginSample

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - uses: whiteducksoftware/azure-arm-action@v1
      with:
        creds: ${{ secrets.AZURE_CREDENTIALS }}
        resourceGroupName: github-action-arm-rg
        templateLocation: ./github-action-deploy-arm-template/template.json
        parameters: ./github-action-deploy-arm-template/parameters.json
```