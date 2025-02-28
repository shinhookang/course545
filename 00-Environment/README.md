# Development Environment

We will utilize a virtual environment for Python 3.11.

For Window users, install WSL2. 

## Install WSL2 

1. Install Windows Terminal from Microsoft Store.

2. WSL2 
Run Termnial in administrator mode.
(Windows + S, search Terminal, Right-click to run in administrator mode.)
Type the following commands:
```
$ wsl —install 
$ wsl --set-default-version 2
```

3. Install Ubuntu Linux from Microsoft Store
ID: kus2025, PASSWD: kus2025

4. Check the WSL version 
```
$ wsl -l -v 
```
If version is 1, then try 
```
$ wsl --set-version Ubuntu 2
$ wsl -l -v 
```

5. Update Ubuntu distribution
```
sudo apt update
sudo apt upgrade
sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl git \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

### How to Access your Linux files
Run the following command in the shell within WSL:
```
explorer.exe .
```
Alternatively, you can directly access the files at `\\wsl.localhost\Ubuntu` in Explorer.

Creating a symbolic link can be useful.
You can do so with the following command:
```
ln -s /mnt/c/Users/brock/Downloads/ ~/downloads
```
Here, 'brock' represents my user ID-be sure to replace it with your own. 


## Install Python 3.11

1. Install `Pyenv` and Set up your shell environment for `Pyenv`

For mac users, 
```bash
brew update
brew install pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init - zsh)"' >> ~/.zshrc
source ~/.zshrc
```

For Windows WSL users,
```bash
curl https://pyenv.run | bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

Check **shims** in PATH variable.
```bash
$> echo $PATH
/Users/Shinhoo/.pyenv/shims:/
```

Check available Python version by `pyenv install --list`



2. Install python 3.11.0 by `pyenv install 3.11.0`

(Uninstall python 3.11.0 by `pyenv uninstall 3.11.0`)


3. Use installed Python 3.11.0

Check list of python versions `pyenv versions`

Set python 3.11 locally by `pyenv local 3.11.0`

(Undo `pyenv local --unset`)

Check the prefix of `pyenv`
```bash
$> pyenv prefix
/Users/Shinhoo/.pyenv/versions/3.11.0
```

You can set python 3.11 globally by `pyenv global 3.11.0`

(Undo `pyenv global system`)

 
## Create a virtual environment
Create a virtual environment. `python -m venv .venv`

Activate the virtual environment. `source .venv/bin/activate`

Deactivate the virtual environment. `deactivate`


## Install Python Libraries

* numpy
* scipy
* matplotlib
* ipykernel

```bash
pip install --upgrade pip
pip install numpy scipy matplotlib ipykernel
```
(You can uninstall Python library using `pip uninstall numpy`)

Install JAX and JAXLIB for differentiable programming.
If you have NVIDIA gpu, then run the following:
```
pip install --upgrade pip
pip install jaxlib==0.4.28+cuda12.cudnn89 -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html
pip install -U "jax[cuda12_pip]"==0.4.28
```
Otherwise `pip install -U jax` for CPU-only.

Check the installed Python packages by `pip list`

## VSCode in WSL

1. Install Visual Studio Code on Windows.
2. Install Python extension (Press Ctrl+Shift+X, and search for `Python`  by Microsoft)
3. Install WSL extension (Press Ctrl+Shift+X, and search for `WSL`  by Microsoft).
4. Open your project in WSL using `code .`.
5. If VSCode cannot to save files inside your WSL directory, grant the necessary permission with `sudo chown -R brock ~/course545`.
Here, **brock** refers to your user ID, **~/course545** is your working directory-adjust them accordingly. 


<!-- ## Reference [PyEnv](https://github.com/pyenv/pyenv) -->
