# ShowTestVar
An example of a BioLockJ module. It prints the current value of an environment variable.

## To use this module

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

## To expand on this module

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
