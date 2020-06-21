
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



## virtualenv
Install virtualenv via pip:

```bash
$ pip install virtualenv
```
Test your installation:
```bash
$ virtualenv --version
```

Important Links
- https://docs.python-guide.org/dev/virtualenvs/
