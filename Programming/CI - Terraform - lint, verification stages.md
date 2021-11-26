## Auto-format Terraform files according to the canonical Hashicorp HCL coding style
  
    terraform fmt
  
## Verify that the coding style for Terraform files already conforms to the HCL coding style

    terraform fmt -check
  
This is primarily useful for building CI pipelines for Terraform repos.
You may wish to enforce a requirement that every commit has already been run through the `terraform fmt` before the code can be merged. This command will fail if that hasn't happened, so the developer will have to reformat their changes before they can be accepted for merge.

## Syntax-check the Terraform files

    terraform validate
