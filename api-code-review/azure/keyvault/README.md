Version v0.1.0
<!-- BEGIN_TF_DOCS -->
# Create One or more Key Vault in Azure
This Module allows you to create and manage Key Vault in Microsoft Azure.

## Changelog

-   Version `v0.1.0`
    * Published artifact name: `keyvault` 
    * Published artifact version: `0.1.0`
    * New module added.
    
    
## Includes

- main.tf
- variables.tf
- output.tf
- README.md
- versions.tf
- example/main.tf
- example/provider.tf
- example/variables.tf
- example/var-keyvault.auto.tfvars
- example/keyvault-publish.yaml

## Features

This module will:

- Create one or multiple Key Vault in Microsoft Azure.

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
| <a name="provider_local"></a> [local](#provider\_local) | `latest` |

## Module(s) Dependency 

Module "resourcegroup" ("./modules/iac-tf-module-az-resource-group")

## Security Controls

| CATEGORY          | SECURITY STANDARD                                                                                                                                 | SECURITY DEFINITION                                                                                                                                                                       | REQUIRED?   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| Access management | [Enabled for deployment](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/key_vault#enabled_for_deployment)         | Ensure that whether Azure Virtual Machines are permitted to retrieve certificates stored as secrets from the key vault                                                                    | Recommended |
| Data Protection   | Encryption                                                                                                                                        | Ensure that keyvault has encryption setting along with disk encryption key and template deployment                                                                                        | REQUIRED    |
| Access management | [Soft delete retention days](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/key_vault#soft_delete_retention_days) | Allows you to recover or permanently delete a key vault and secrets for the duration of the retention period.                                                                             | REQUIRED    |
| Data Protection   | [Purge protection enabled](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/key_vault#purge_protection_enabled)     | Ensure that keyvault has purge protection enabled                                                                                                                                         | REQUIRED    |
| Access management | authorization                                                                                                                                     | Ensure how SP, application , users or group access the keys, certificates, secrets stored inside Key vault,it has boolean flag & options are RBAC or Access policies                      | Required    |
| Security          | Networking                                                                                                                                        | Network ACLs allow you to reduce your exposure to risk by limiting what can access your key vault.                                                                                        | Recommended |
| Tags              | Tags                                                                                                                                              | Ensure mandatory tags are provided as per client requirements                                                                                                                             | Recommended |
| Access management | Access policy                                                                                                                                     | Ensure list of 16 policies were defined under access policies if enable_rbac_authorization is set to false                                                                                | Optional    |
| Access control    | network access control lists                                                                                                                      | Ensure Nacls are defined as per standards                                                                                                                                                 | Recommended |
| Security          | Private Endpoint                                                                                                                                  | Ensure private endpoint needs to be created  for keyvault                                                                                                                                 | Recommended |

## Resources

| Name | Type |
|------|------|
| [azurerm_key_vault.this](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/key_vault) | resource |
| [azurerm_key_vault_access_policy.current](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/key_vault_access_policy) | resource |
| [azurerm_key_vault_access_policy.this](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/key_vault_access_policy) | resource |
| [azurerm_role_assignment.keyvault_admin](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/role_assignment) | resource |
| [azurerm_role_assignment.this](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/resources/role_assignment) | resource |
| [azuread_groups.rbac](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/groups) | data source |
| [azuread_groups.this](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/groups) | data source |
| [azuread_service_principals.rbac](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/service_principals) | data source |
| [azuread_service_principals.this](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/service_principals) | data source |
| [azuread_users.rbac](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/users) | data source |
| [azuread_users.this](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/users) | data source |
| [azurerm_client_config.current](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/data-sources/client_config) | data source |
| [azurerm_resource_group.this](https://registry.terraform.io/providers/hashicorp/azurerm/3.3.0/docs/data-sources/resource_group) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_access_policies"></a> [access\_policies](#input\_access\_policies) | Manages a Key Vault Access Policy. | <pre>map(object({<br>    key_vault_name          = string<br>    service_principal_names = list(string)<br>    user_names              = list(string)<br>    group_names             = list(string)<br>    key_permissions         = list(string)<br>    secret_permissions      = list(string)<br>    certificate_permissions = list(string)<br>    storage_permissions     = list(string)<br>  }))</pre> | `{}` | no |
| <a name="input_key_vaults"></a> [key\_vaults](#input\_key\_vaults) | Specifies values for Key Vault network access | <pre>map(object({<br>    key_vault_name                  = string<br>    resource_group_name             = string<br>    enabled_for_deployment          = bool<br>    enabled_for_disk_encryption     = bool<br>    enabled_for_template_deployment = bool<br>    enable_rbac_authorization       = bool<br>    soft_delete_retention_days      = number<br>    purge_protection_enabled        = bool<br>    sku_name                        = string<br>    additional_tags                 = map(string)<br>    network_acls = object({<br>      bypass                     = string      <br>      default_action             = string       <br>      ip_rules                   = list(string) <br>      virtual_network_subnet_ids = list(string) <br>    })<br>  }))</pre> | `{}` | Yes |
| <a name="input_role_assign"></a> [role\_assign](#input\_role\_assign) | Manages role assignment | <pre>map(object({<br>    key_vault_name          = string<br>    service_principal_names = list(string)<br>    user_names              = list(string)<br>    group_names             = list(string)<br>    role_definition_name    = string<br>  }))</pre> | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_keyvaults"></a> [keyvaults](#output\_keyvaults) | Describes keyvault id and uri |