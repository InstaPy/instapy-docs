# Install Build Tools
Even though _Python_ is an _**interpreted** language_, you may need to install _Windows_ _C++_ **compilers** in some cases.  
Unlike _Linux_, compilers for _Windows_ are not included **by default** in the OS.  

_For example_, you will need to use them if you **wish** to: 
 - Install a non-pure _Python_ package from sources by [**pip**](https://pip.pypa.io/) (_if there is no [_wheel_](http://wheel.readthedocs.org/) package provided_).   

<br />

<details>
  <summary>
    <b>
      <i>Such as</i>, let's take the <i>regex</i> package that we use 🔎  
    </b>
  </summary>

It has a _non-Python_ code which must be **compiled** before installing.  
They provide _**built** binary wheels_ for both _32-bit_ and _64-bit_ versions of _Windows_ OS who has _Python_ 3.5+ installation.  
Other platforms **and** also systems with python versions _below_ that has to install the package from its **source**.

</details>


## _Windows_ OS
Microsoft provides official _C++_ compilers called _Visual C++_, you can find them bundled with _Visual Studio_ or, for some versions, in standalone distributions.  
### Microsoft _Visual C++_ 14.0 standalone: **Build Tools** for _Visual Studio_ 2017 (_**x86**, **x64**, **ARM**, **ARM64**_)  
This is a standalone version of _Visual C++_ 14.0 compiler, you don't need to install _Visual Studio_ 2017. 

- Install 🧰 [Microsoft **Build Tools** for _Visual Studio_ 2017](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2017).  
- The **setuptools** _Python_ package version must be at least 34.4.0. 

Restart PC (_recommended_)

>**Note**: The compiler's **architecture** must be _the same_ as Python's (_for example: if you use _Python_ 64-bit, you have to use an x64 compiler_). 

You should know that, _Visual C++_ 14.0 is **intended for** _Python_ 3.5+.   
If you have an **older** _Python_, visit the [WindowsCompilers](https://wiki.python.org/moin/WindowsCompilers) _Python_ wiki-page to get the compiler version that **corresponds** to your _Python_ version.

## _Mac_ OS X
Generally, it also provides **build tools** by default like in _Linux_.   
But once users **upgrade** their OS, they might need to install it **again**.

You must install the appropriate version of the _Command Line Tools_ - **XCode** for your _Mac_ OS.  
- Install 🧰 it running,
```erlang
xcode-select --install
```
- Also, you can run,
```erlang
xcode-select -print-path
```
to see your _active_ **developer path**.

