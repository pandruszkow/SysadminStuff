## Object IDs

Made up of two components: the type, and the name.

So an `aws_instance` named `jumphost` would be identified by `aws_instance.jumphost` in all subsequent references from the tf file and from the command line

## Mark an object for replacement

Use `terraform taint <object_id>`

