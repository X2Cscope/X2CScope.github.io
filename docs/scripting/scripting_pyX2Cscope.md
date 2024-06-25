---
layout: default
title: Scripting pyX2Cscope
nav_order: 4
has_children: false
---

<a href="https://x2cscope.github.io/pyx2cscope/"> <img src="../../images/pyx2cscope_logo.png" alt="LOGO" align="left" style="padding-right: 15px" width="150"/> </a>

pyX2Cscope is the PC side software implementatio to communicate to the X2C firmware enabled platforms.

Detailed documentation of pyX2Cscope python package: [https://x2cscope.github.io/pyx2cscope/](https://x2cscope.github.io/pyx2cscope/)


# Quick start

Create a virtual environment and install pyx2cscope using the following commands (Windows):

```bash
python -m venv .venv
.venv\Scripts\activate
pip install pyx2cscope
```

It is highly recommended to install python libraries underneath a virtual environment.

Nevertheless, to install at system level, execute the following lines:

```bash
pip install pyx2cscope
pip install PyQt5 --user --ignore-installed
```

In case you already have installed pyx2cscope, you only need to update the package to the new version typing:

```bash
pip install --upgrade pyx2cscope
```

Start pyX2Cscope

```bash
# Start demo QT based GUI
python -m pyx2cscope
```

```bash
# Start WEB based GUI
python -m pyx2cscope -w
```

```bash
# Help
python -m pyx2cscope --help
```

![pyX2Cscope animation](../../images/pyx2cscopeConsole.gif)