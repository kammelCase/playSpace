Version v0.1.0
<!-- BEGIN_TF_DOCS -->
# Create Resource group
This module allows you to create one or more resource groups.

## Changelog

-   Version `v0.1.0`
    * Published artifact name: `resourcegroup` 
    * Published artifact version: `0.1.0`
    ---

## Includes

-   main.tf      
-   variables.tf  
-   output.tf   
-   README.md   
-   versions.tf
-   example/main.tf  
-   example/provider.tf
-   example/variables.tf  
-   example/var-resourcegroup.auto.tfvars
-   example/resourcegroup-publish.yaml

## Features  

This module will:

-   Create and manage one or multiple Resource Group in Microsoft Azure

## How to use?
* Azure DevOps:
    1. Copy `var-{module.name}.auto.tfvars` file in environment folder of your repository/branch. 
    2. Rename it to `var-${tfvars_file_name}.auto.tfvars` if required.
    3. Modify values of the attributes if required. And commit changes if any.
    4. Go-to `Pipline.{env}.yaml` file and add resource block if it is not there. And commit changes.
    5. Execute the pipeline by selecting `{tfvars_file_name}_plan` or `{tfvars_file_name}_apply` or both.
    
    ---

* GitLab:
    1. Copy contains of `example/main.tf` file
    2. Open gitlab. Move to required `{organization}/{project}/{subproject}/{dir_if_any}`.
    3. Create a new file say `main.tf`. Paste what you copied from `example/main.tf`
    4. Check source and modify value of attributes if required. Commit changes.
    5. Create a new file `provider.tf` in same directory and paste the contains of `example/provider.tf` there.
    6. Make required changes in `.gitlab-ci.yml` file and execute the pipeline.
    
    ---

* Local:
    1. Clone the repo to local.
    2. Make sure to setup terraform and environment paths correctly
    3. (For testing module) Open terminal inside example folder and run terraform commands provided below. (change `source = "../"`)
    4. (For using this module) Copy code from the example/main.tf, give path to the module in "source".
    6. Modify value of attributes if required.
    5. In same directory where module is being called, open terminal and run terraform commands provided below.
    6. Terraform commands: `terraform init` -> `terraform plan` -> `terraform apply`

    ---

## Requirements
| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | `1.1.9` |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | `3.3.0` |

## Security Controls

| CATEGORY | SECURITY STANDARD | SECURITY DEFINITION                                           | REQUIRED?   |
| -------- | ----------------- | ------------------------------------------------------------- | ----------- |
| Tags     | Tags              | Ensure mandatory tags are provided as per client requirements | Recommended |

## Resources

| Name | Type |
|------|------|
| [azurerm_resource_group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/resource_group) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_resource_group"></a> [resource\_group](#input\_resource\_group) | ResourceGroups | <pre>map(object({<br>        rg_name = string<br>        location = string<br>        tags = map(string)<br>    }))</pre> | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_resource_group_id"></a> [resource\_group\_id](#output\_resource\_group\_id) | Outputs a map of resource group names with there respective resource Ids |
<!-- END_TF_DOCS -->