
## Before you begin

This project is an example of a [BioLockJ](https://github.com/BioLockJ-Dev-Team/BioLockJ) module. 

To build it, or even just to use it, you must have successfully installed and tested [BioLockJ](https://github.com/BioLockJ-Dev-Team/BioLockJ).
```
biolockj --version
biolockj ${BLJ}/templates/myFirstPipeline/myFirstPipeline.properties
```

For more information about how to create BioLockJ modules and for other examples, see [the BioLockJ external modules resource repository](https://github.com/BioLockJ-Dev-Team/blj_ext_modules)

### Use this module

See the [userguide pages for the modules in this project](mkdocs/docs/index.md).

Download the jar file to your external modules folder (`mods`), which you point to with the `--external-modules` argument.  In your config file, reference the ShowBljVars module in your module run order using the `#BioModule` keyword.

Minimalist example:
```
mkdir ShowTestVar_Example
cd ShowTestVar_Example
mkdir mods
mkdir demo
cd mods
wget https://github.com/BioLockJ-Dev-Team/ShowTestVar/releases/download/0.0.0/ShowTestVar.jar
cd ../demo
wget https://raw.githubusercontent.com/BioLockJ-Dev-Team/ShowTestVar/main/demo/printBlj.config
cd ..
biolockj --external-modules $PWD/mods ./demo/printBlj.config
```
The example above will create a minimalist pipeline deomonstrating the use of the ShowBljVars module from the ShowTestVar project.  

Add the `#BioModule` line for the ShowBljVars module to any other pipeline.

### Build this module

The build file references the BioLockJ project by assuming it is a peer folder.
```
cd $BLJ
cd ..
git clone https://github.com/BioLockJ-Dev-Team/ShowTestVar.git
cd ShowTestVar
ant
```

_If you encounter build difficulties, try using the docker build process below._

Test that BioLockJ recognizes the module.
```
biolockj-api listModules --external-modules $PWD/dist
```
The output list should include "com.github.fodorlab.envVar.ShowTestVar".

Run a demo pipeline.
```
biolockj --external-modules $PWD/dist ./demo/printBlj.config
```

Check the demo folder for more examples.

### Build the project and its documentation using docker
Confirm docker is running:
```
docker run --rm hello-world
```

Note: the code block below references this project directory as `$PWD`.
```
cd ShowTestVar
```

This is the standard build process for BioLockJ modules.
```
docker run --rm \
  -v $PWD:/project \
  -v $BLJ:/BioLockJ \
  -e BLJ=/BioLockJ \
  -w /project \
  biolockjdevteam/build_and_deploy \
  ant userguide
```

This process produces the jar file and the standardized [userguide pages](mkdocs/docs/index.md) for the modules in this project.

-------

## This is a template

This project has all the components we typically expect to see for a third-party BioLockJ module.

Notice that this repository is a template repository. To make your own BioLockJ module, you can copy this reposiotry to start from its files and structure, test the build process, and modify from there to make your own module.  

Run through the instructions below to make sure your system is set up correctly to run BioLockJ and use external modules.  

In your own copy of this README, delete the section "This is a template", and update other instructions to reference your own repo.
