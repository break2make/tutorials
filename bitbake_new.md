**What is the layout of a bitbake project?**

- Layer folder: A layer folder contains configuration, task and target descriptions for what BitBake does. It is common practice to name a layer folders meta-'something'.
- Build folder: The build folder is the directory from which the bitbake command has to be executed.

**What are the important file types?**
- build/conf/bblayers.conf
- base.bbclass
- bitbake.conf
- meta-layer_name/conf/layer.conf

**What is the order of reading these files?**

- The first file that BitBake expects, is conf/bblayers.conf in its working directory, which is our build directory.
    build/conf/bblayers.conf
    ```
    BBPATH := "${TOPDIR}"
    BBFILES ?= ""
    BBLAYERS = "${TOPDIR}/../meta-tutorial"
    ```
    `BBLAYERS` specifies the path to each layer folder.
- meta-tutorial/conf/layer.conf. Each layer needs a conf/layer.conf file having at least following informations:
    ```
    BBPATH .= ":${LAYERDIR}"
    BBFILES += ""
    ```
    `BBPATH` specifies the top directory of a layer, and `BBFILES` spcifies the recepies.
  
**What is the bitbake search path?**
For BitBake there are some file paths which are relative to BBPATH. This means that if we tell BitBake to search for some path then it will search all directives in BBPATH for somedir/somefile. We have added TOPDIR and LAYERDIR to BBPATH, so classes/base.bbclass and conf/bitbake.conf could be in any of them.


  
