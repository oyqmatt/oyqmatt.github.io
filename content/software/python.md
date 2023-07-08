---
title: "Python"
date: 2023-07-03T21:53:06+08:00
weight: 2
---

## Virtualenv and Virtualenvwrapper

My preferred virtual env manager.

### Installation

```
sudo apt install python3-pip
pip3 install virtualenv virtualenvwrapper
```

Add to ~/.bashrc
```
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
source ~/.local/bin/virtualenvwrapper.sh
```

