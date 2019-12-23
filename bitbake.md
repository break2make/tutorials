
Command to execute a specific task of a recipe:

```bash
$ bitbake <recipe-name> -c <task-name>
```



- BitBake first searches the current working directory for an optional `conf/bblayers.conf` configuration file. This file is expected to contain a `BBLAYERS` variable that is *a space delimited list of 'layer' directories*. Recall that if BitBake cannot find a bblayers.conf file then it is assumed the *user has set the BBPATH and BBFILES directly in the environment*.

- For each directory (layer) in this list, a conf/layer.conf file is searched for and parsed with the LAYERDIR variable being set to the directory where the layer was found. The idea is these files automatically setup BBPATH and other variables correctly for a given build directory.

- BitBake then expects to find the conf/bitbake.conf file somewhere in the user-specified BBPATH. That configuration file generally has include directives to pull in any other metadata such as files specific to the architecture, the machine, the local environment, and so forth.

> **NOTE:** 
Only variable definitions and include directives are allowed in `.conf` files. Some variables directly influence BitBake's behavior. These variables might have been set from the environment depending on the environment variables previously mentioned or set in the configuration files. The "Variables Glossary" chapter presents a full list of variables.

- The base.bbclass file is always included. Other classes that are specified in the configuration using the INHERIT variable are also included. BitBake searches for class files in a "classes" subdirectory under the paths in BBPATH in the same way as configuration files.

- A good way to get an idea of the configuration files and the class files used in your execution environment is to run the following BitBake command:

     $ bitbake -e > mybb.log
            
Examining the top of the mybb.log shows you the many configuration files and class files used in your execution environment.


# Understanding build time dependencies DEPENDS and run time dependencies RDEPENDS

>source: https://www.lynxbee.com/understanding-compile-time-dependencies-depends-and-run-time-dependencies-rdepends-in-yocto-recipe/

_Most software packages have a short list of other packages that they require, which are called dependencies. These dependencies fall into two main categories: build-time dependencies, which are required when the software is built; and runtime dependencies, which are required to be installed on the target in order for the software to run._

Within a recipe, you specify build-time dependencies using the DEPENDS variable. Although nuances exist, items specified in DEPENDS should be names of other recipes. It is important that you specify all build-time dependencies explicitly. If you do not, due to the parallel nature of BitBake’s execution, you can end up with a race condition where the dependency is present for one task of a recipe (e.g. do_configure) and then gone when the next task runs (e.g. do_compile).

Another consideration is that configure scripts might automatically check for optional dependencies and enable corresponding functionality if those dependencies are found. This behavior means that to ensure deterministic results and thus avoid more race conditions, you need to either explicitly specify these dependencies as well, or tell the configure script explicitly to disable the functionality. If you wish to make a recipe that is more generally useful (e.g. publish the recipe in a layer for others to use), instead of hard-disabling the functionality, you can use the PACKAGECONFIG variable to allow functionality and the corresponding dependencies to be enabled and disabled easily by other users of the recipe.

Similar to build-time dependencies, you specify runtime dependencies through a variable – RDEPENDS, which is package-specific. All variables that are package-specific need to have the name of the package added to the end as an override. Since the main package for a recipe has the same name as the recipe, and the recipe’s name can be found through the ${PN} variable, then you specify the dependencies for the main package by setting RDEPENDS_${PN}. If the package were named ${PN}-tools, then you would set RDEPENDS_${PN}-tools, and so forth.

Some runtime dependencies will be set automatically at packaging time. These dependencies include any shared library dependencies (i.e. if a package “example” contains “libexample” and another package “mypackage” contains a binary that links to “libexample” then the OpenEmbedded build system will automatically add a runtime dependency to “mypackage” on “example”).

>source: https://stackoverflow.com/questions/30802811/bitbake-runtime-vs-build-dependency/30847513

As you say, bitbake is concerned with building and deploying the packages, and it needs to deploy all the packages that are needed to satisfy runtime dependencies on the target system.

If your recipe says that target T DEPENDS on a target P, that tells bitbake that it must build P before T, because T can't be built without P.

If your recipe says that T RDEPENDS on P, that tells bitbake that it must deploy P to the target system if it deploys T, because T can't be used without P.

For example, you can't build tar without the C compiler, but you don't need the C compiler to use tar. You can deploy tar without deploying the C compiler. So that's a DEPEND.

On the other hand, you can't use tar without the runtime C library. If tar is deployed, the runtime C library must also be deployed. So that's an RDEPEND.

The bitake technicalities are:

If T DEPENDS on P then T's do_configure task is made to depend on P's do_populate_sysroot task.

If T RDEPENDS on P then T's do_build task ia made to depend on P's do_package_write task.


# Links
- https://a4z.bitbucket.io/docs/BitBake/guide.html
- https://www.yoctoproject.org/docs/1.6/bitbake-user-manual/bitbake-user-manual.html#var-RDEPENDS
- http://wiki.openmoko.org/wiki/BitBake_recipe
- https://stefanchrist.eu/blog/2017_09_15/Yocto%20Recipes%20vs%20Packages.xhtml
- https://wiki.koansoftware.com/index.php/Bitbake_options
- https://wiki.rdkcentral.com/display/RDK/Yocto+Developer%27s+Guide
- https://subscription.packtpub.com/book/virtualization_and_cloud/9781788399210/1/ch01lvl1sec27/debugging-the-build-system
- https://www.yoctoproject.org/docs/what-i-wish-id-known/

