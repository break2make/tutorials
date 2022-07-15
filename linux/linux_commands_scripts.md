

###  How to source a bash script from a chs shell?

```bash
$ bash -c "source script_name.sh; exec csh"
```

### How to compress a whole directory (including subdirectories) using TAR in Unix based OS with the CLI

```bash
tar -zcvf [result-filename.tar.gz] [path-of-directory-to-compress]
```
The -zcvf instruction stand for:

-z: Compress the desired file/directory using gzip

-c: Stand for create file (output tar.gz file)

-v: To display the progress while creating the file

-f: Finally the path of the desire file/directory to compress

For example, let's suppose that you are located in the command line in the /www directory and inside this directory there is a folder that you want to compress into a single file namely "sandbox". To compress the sandbox folder into a tar file you would run the command as:

```bash
tar -zcvf sandbox_compressed.tar.gz sandbox
```

This should start the compression of the directory into a new tar file, as we have our -v argument to display the progress in the console, you would see a list of every filename that is being added to the file.

**Extracting generated file** 

If you want now to extract as well with the command line the generated file, you should use now the following command syntax:

```bash
tar -xvzf [your-tar-file.tar.gz]
```

The -zcvf instruction stands for:

-z: Compress the desired file/directory using gzip

-x: Stand for extract file (input tar.gz file). If any files are named on the command line, only those files will be extracted from the archive.

-v: To display the progress while creating the file

For example, to extract our previously created file you should use the command:

```bash
tar -xvzf sandbox_compressed.tar.gz
```

That will extract the content of the file (sandbox folder) in the current directory.


**Extracting content to a custom directory**

If you need to extract the content of the generated tar to a custom directory instead of the current directory, you can specify the new directory where the content should be extracted using the -C or --directory option in your extraction command:

```bash
tar -xvzf sandbox_compressed.tar.gz -C /target/directory
```