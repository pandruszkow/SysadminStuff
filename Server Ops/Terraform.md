## Object IDs

Made up of two components: the type, and the name.

So an `aws_instance` named `jumphost` would be identified by `aws_instance.jumphost` in all subsequent references from the tf file and from the command line

## Apply a Terraform change only to selected objects

Assuming that changes were made to `aws_instance.example`, but also a number of other resources, you can selectively apply changes to just `aws_instance.example` by running:

    terraform apply -target=aws_instance.example
    
Take care not to use this too often, or you risk putting your Terraform state into something undefined (or perhaps even risk creating dependency cycles) that's hard to recover from.

## Mark an object for replacement

Use:
    
    terraform taint <object_id>

## Rename an object

When you rename an already-created object in the source code, TF will attempt to destroy and create it again. The way to avoid that is to run:

    terraform state mv <old_object_id> <new_object_id>
  
And then rename the object in your source code. Running `terraform plan` or `apply` afterwards should show that no changes have to be made. 
