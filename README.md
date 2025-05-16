# CICD-Terraform

**This is to automate aws infra deployment using GitHub action.
**
**CI tool: GitHub Actions
**It’s responsible for continuously integrating changes to your Terraform code—checking out the repo, linting/validating your .tf files, running terraform fmt/validate/plan, and reporting back on whether everything looks good.

**CD tool: Terraform
**Once your GitHub Actions workflow approves the plan, Terraform (via its apply step) is what actually deploys or updates your infrastructure on AWS—i.e. the “continuous deployment” of your infra.
