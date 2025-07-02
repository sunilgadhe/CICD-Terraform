# CICD-Terraform-Pipeline

**This is to automate aws infra deployment using GitHub action.
**
**CI tool: GitHub Actions
**It’s responsible for continuously integrating changes to your Terraform code—checking out the repo, linting/validating your .tf files, running terraform fmt/validate/plan, and reporting back on whether everything looks good.

**CD tool: Terraform
**Once your GitHub Actions workflow approves the plan, Terraform (via its apply step) is what actually deploys or updates your infrastructure on AWS—i.e. the “continuous deployment” of your infra.


/////////
backend.tf
/////////

// Define Terraform configuration
TerraformConfiguration {
  
  // Configure state storage backend
  Backend ofType "s3" {
    // Name of the S3 bucket where state is stored
    bucketName      = "sunil-tf-file"
    
    // AWS region for the bucket
    bucketRegion    = "us-east-1"
    
    // Path/key within the bucket for the tfstate file
    stateFileKey    = "s3-github-actions/terraform.tfstate"
    
    // Whether to encrypt the state file at rest
    enableEncryption = true
  }

  // Specify the minimum Terraform version required
  MinimumTerraformVersion = "0.13.0"

  // Declare providers that Terraform will use
  RequiredProviders {
    
    // AWS provider configuration
    Provider "aws" {
      // Minimum provider version
      versionConstraint = "2.7.0"
      
      // Source registry for the provider
      sourceLocation   = "hashicorp/aws"
    }
  }
}
