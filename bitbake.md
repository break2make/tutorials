
Command to execute a specific task of a recipe:

```bash
$ bitbake <recipe-name> -c <task-name>
```



- BitBake first searches the current working directory for an optional `conf/bblayers.conf` configuration file. This file is expected to contain a `BBLAYERS` variable that is *a space delimited list of 'layer' directories*. Recall that if BitBake cannot find a bblayers.conf file then it is assumed the *user has set the BBPATH and BBFILES directly in the environment*.

- For each directory (layer) in this list, a conf/layer.conf file is searched for and parsed with the LAYERDIR variable being set to the directory where the layer was found. The idea is these files automatically setup BBPATH and other variables correctly for a given build directory.

- BitBake then expects to find the conf/bitbake.conf file somewhere in the user-specified BBPATH. That configuration file generally has include directives to pull in any other metadata such as files specific to the architecture, the machine, the local environment, and so forth.


> **NOTE:** 
Only variable definitions and include directives are allowed in `.conf` files. Some variables directly influence BitBake's behavior. These variables might have been set from the environment depending on the environment variables previously mentioned or set in the configuration files. The "Variables Glossary" chapter presents a full list of variables.
