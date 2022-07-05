# Argument parsing / validation of runtime requirements

## Validate number of arguments
Assuming you want to call `_usage` function and then exit with an error code if the script was called with fewer than 2 mandatory arguments:

```sh
if [ "$#" -lt 2 ]; then
        _usage
        exit -1
fi
```

## Checking if the script is running as root
Assuming you want to exit the script with an error code if the script was not run with root privileges:
```sh
if [ $(id -u) != 0 ]; then
	echo "This script must be run as root."
	exit -1
fi
```
