# Azure Landing Zone Spoke Template

This template is designed to be used programmatically to create repositories for the spokes in the Azure Landing Zone.

## New Spoke Repository

The process has the following steps:

1. Create Azure Subscriptions for DEVL, PREPROD, PROD
2. Create Azure DevOps Project
3. Create Service Principals/Managed Identities in Azure
4. Create Service Connections in Azure DevOps Project
5. Create this repository.

## Azure Landing Zone

The main repository for the Azure Landing Zone, staff-infrastructure-azure-landing-zone, can be found [here](https://github.com/ministryofjustice/staff-infrastructure-azure-landing-zone)

If you have a Confluence account, you can look at the [LLD](https://dsdmoj.atlassian.net/wiki/spaces/PTTPWIK/pages/2875556181/Azure+Landing+Zone+LLD) too which, though the code should be considered the ultimate source of the truth.

The Azure Landing Zone uses Github for source control and [Azure DevOps](https://dev.azure.com/MoJ-OFFICIAL/) for Pipelines.

 ## Contents

The MoJ's own [format-code github action](https://github.com/ministryofjustice/github-actions/tree/main/code-formatter) is used to format terraform code.

The templates directory has a template that the ALZ team uses for deployment Terraform code to Azure.

This template [terraform-deployment.yml](templates/terraform-deployment.yml) has two distinct run modes:

### Pull Request

- install terraform
- run
  - terraform init
  - terraform validate
  - terraform plan
  - Plan will be posted as a comment to the PR
  - Checkov
  - If checkov detects anything, this will be posted as a comment to the PR

### CI

- install terraform
- run
  - terraform init
  - terraform validate
  - terraform plan
  - terraform apply


The template makes use of the [AddGitHubPrComment.ps1](scripts/AddGitHubPrComment.ps1) script to post the comments to the PR.

The script will also minimize old comments, namely from previous runs of the pipeline and in order to do this, it requires a PAT from a github account with permissions to write comments.


Once the repository has been handed over to you please:

* Edit the copy of this README.md file to document your project
* Grant permissions to the appropriate MoJ teams
* Setup branch protection


