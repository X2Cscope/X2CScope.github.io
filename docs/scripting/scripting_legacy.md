---
layout: default
title: Scripting (legacy MPLAB X)
nav_order: 6
has_children: true
---

# New python implementation!

The new recommended Python implementation for scripting interfaces can be found at pyx2cscope: https://x2cscope.github.io/pyx2cscope/

!The documentation below is for the not maintained MPLAB X plugin!

# Legacy MPLAB X plugin scripting summary:

X2Cscope can run scripts with the help of Java and netbeans platform. It supports Python 2 (Jython engine) and Javascript (Java nashorn engine).

X2Cscope plugin exports 2 interfaces:
1. `public interface ISymbolManager`
2. `public interface IScopeManager`

Before the selected script is executed, 2 variables with the type of these interfaces are getting initialised. This is for abstraction and user convinience. The two prepared objects that can be used without initialisation:

   * [**x2c_symbol**](scripting_watch.md) Access to global variables directly via scripting.
   
   * [**x2c_scope**](scripting_scope.md) Access global variables via a virtual scope and monitor them.

## Examples

Script examples are included within the demo applications. See the [Demos/Download page](../supportedHW.md).

## Python syntax highlight in MPLAB X

1. Download the python package for Netbeans: http://plugins.netbeans.org/plugin/56795/python4netbeans802
2. Install the org-netbeans-modules-python-editor.nbm from the package.
   1. Tools-->Plugins-->Downloaded-->Add Plugin..
   2. Install
   3. Restart MPLAB X