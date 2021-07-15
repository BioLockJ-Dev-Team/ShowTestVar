# ShowTestVar
An example of a BioLockJ module. It prints the current value of an environment variable.

See the [documentation for the modules in this project](mkdocs/docs/index.md).

## This is a template

This project has all the components we typically expect to see for a third-party BioLockJ module.

Notice that this repository is a template repository. To make your own BioLockJ module, you can fork this repository to copy its files and structure, test the build process, and modify from there to make your own module.  

Run through the instructions below to make sure your system is set up correctly to run BioLockJ and use external modules.  

In your own copy, delete everything from "This is a template" in this README.

### Use this module

Download the jar file to your external modules folder (`mods`).

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
biolockj --external-modules ./mods ./demo/printBlj.config
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

Test that BioLockJ recognizes the module.
```
biolockj-api listModules --external-modules ./dist
```
The output list should include "com.github.fodorlab.envVar.ShowTestVar".

Run a demo pipeline.
```
biolockj --external-modules $PWD/dist ./demo/printBlj.config
```

See more in the demo folder.
