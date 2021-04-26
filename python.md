
# Arbitrary code execution with Python pickles

Read the following links:
- https://checkoway.net/musings/pickle/
- https://root4loot.com/post/exploiting_cpickle/
- https://blog.nelhage.com/2011/03/exploiting-pickle/


# Default python setup

Use the following commands in Ubuntu to configure a default python setup.

For python3:

```bash
echo "alias python=python3" >> ~/.bashrc
```
```bash
echo "alias pip=pip3" >> ~/.bashrc
```

For python2:

```bash
echo "alias python=python2" >> ~/.bashrc
```
```bash
echo "alias pip=pip2" >> ~/.bashrc
```



Then refresh your terminal again:
```bash
source ~/.bashrc
```

# Python virtual environment

## Install virtualenv
Install virtualenv via pip:

```bash
$ pip install virtualenv
```
Test your installation:
```bash
$ virtualenv --version
```

## Create a virtual env

```
$ virtualenv -p </usr/bin/python3.8> ./.venv [--always-copy]
```

Options:
- `-p` to specify the a specific version of python for your vurtual environment
- --always-copy to avoid the symbolic link copy problem. `I found a problem without `--always-copy` while trying to create virtual environment in virtualbox shared folder in Ubuntu 20.04`.

## Srtat using .venv
To begin using the virtual environment, it needs to be activated:

```
$ source .venv/bin/activate
```
Assuming that you are in your project directory:

...\project_folder> venv\bin\activate
Install packages using the pip command:

```
$ pip install requests
```
If you are done working in the virtual environment for the moment, you can deactivate it:

```
$ deactivate
```


# Web frameworks

## Flask

```
<.venv> $ pip3 install Flask
```

```
<.venv> $ python -m flask --version
```

Important Links
- https://docs.python-guide.org/dev/virtualenvs/
