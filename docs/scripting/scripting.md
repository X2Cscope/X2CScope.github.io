---
layout: default
title: Scripting
nav_order: 5
has_children: true
---

# Summary 

X2Cscope can run scripts with the help of Java and netbeans platform. It supports Python 2 (Jython engine) and Javascript (Java nashorn engine).

X2Cscope plugin exports 2 interfaces:
1. `public interface ISymbolManager`
2. `public interface IScopeManager`

Before the selected script is executed, 2 variables with the type of these interfaces are getting initialised. This is for abstraction and user convinience. The two prepared objects that can be used without initialisation:

   * [**x2c_symbol**](scripting_watch.md) Access to global variables directly via scripting.
   
   * [**x2c_scope**](scripting_scope.md) Access global variables via a virtual scope and monitor them.

## Examples

Script examples are included within the demo applications. See the [Demos/Download page](../supportedHW.md).