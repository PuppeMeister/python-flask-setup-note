# Pyenv with Virtualenv and VirtualEnv Wrapper Setup in WSL2

Since using windows as python developing environment is kinda complicated, I decided to utilizes WSL2 to create the isolated environment. However per 17 December 2021
Upgrading the default python version in WSL2 (in this case, I choose Ubuntu) is still unsuccessful.
In order not to forget every steps, here I documented my installation steps.

## 1. Preparing the required dependencies of Pyenv

Check the python3 and pip3 version by typing

```
$ python3 --version
```

and 

```
$ pip3 --version
```
for knowing which directory python3 using, use

```
whereis python3
```

Installed the required dependencies by typing this command below.

```
$ sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl
```

## 2. Installing Pyenv with Curl Command

```
curl https://pyenv.run | bash
```
The command above will install pyenv along with these other packages below:

- pyenv-virtualenv (pyenv virtualenv built-in)
- pyenv-update (pyend updating plugin)
- pyenv-doctor (verificating plugin for pyenv and its installed dependencies)
- pyenv-which-ext (enable pyenv to lookup for system commands automatically)

## 3. Insert additional variables to .bashrc

```
$ echo export PATH='"$HOME/.pyenv/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(pyenv init -)"' >> ~/.bashrc 
$ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
```

## 4. Reload ~/.bashrc script

```
source ~/.bashrc
```

## 5. Ensure the Installation works

```
$ pyenv --version
```

## 6. Install Virtual Env Wrapper

```
$ sudo pip3 install virtualenvwrapper
```

## 7. Adding this additional variable to /.bashrc

```
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON='/usr/bin/python3'
source /usr/local/bin/virtualenvwrapper.sh
```

## 8. Test the wrapper by creating a new virtual environment

```
$ mkvirtualenv [NAME-OF-THE-NEW-VIRTUAL-ENVIRONMENT]
```

## 9. Activate and deactivate virtual environment

```
$ workon [NAME-OF-THE-NEW-VIRTUAL-ENVIRONMENT]
```

```
$ deactivate
```

## 10. After Installation

Adding another python packages can be done by running usual pip command. The isolated virtual environment can be accessed
through ''python interpreter'' setup in Pycharm (in case using Pycharm).

## References
1. https://realpython.com/intro-to-pyenv/
