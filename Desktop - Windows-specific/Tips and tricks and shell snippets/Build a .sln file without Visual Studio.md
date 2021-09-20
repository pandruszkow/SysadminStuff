# Building a `.sln` file on Windows without Visual Studio

1. Find out where the file `MSBuild.exe` is located on your machine. It's most likely at `C:/Windows/Microsoft.NET/Framework/v<installed .NET version>/MSBuild.exe`.
2. Open a command line window and `cd` to the directory with the `.sln` file
3. Run `<full path to MSBuild.exe> <filename>.sln`
4. You should get the compiled binary in the usual location, under `bin/Debug` in the project folder
