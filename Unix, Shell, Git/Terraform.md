## Object IDs

Made up of two components: the type, and the name.

So an `aws_instance` named `jumphost` would be identified by `aws_instance.jumphost` in all subsequent references from the tf file and from the command line

## Mark an object for replacement

Use `terraform taint <object_id>`

## Rename an object

When you rename an already-created object in the source code, TF will attempt to destroy and create it again. The way to avoid that is to run:

  terraform state mv aws_something.old_name aws_something.new_name
  
And then rename the object in your source code. Running `terraform plan` or `apply` afterwards should show that no changes have to be made. 
