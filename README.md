# Introduction
I made this template for personal use, and i configured it only for windows and xc8 compiler 
# Requirements
* C/C++ Extension installed
* xc8 Compiler installed
* prjMakeFilesGenerator installed (comes with MPLAB X IDE)
* gnuWin32 tools installed (comes with MPLAB X IDE)

# Initialization

After importing this template in vscode you must do the following in order to successfully compile your source code using make

1. Configure Environment variables for gnuWin32

Add path of gnuWin32 to the Path system environment variable 
gnuWin32 comes with MPLAB X IDE and located at `$InstallDir\gnuBins\GnuWin32\bin`

2. Configure C/C++ Extension

For intellisense to work properly you should edit env variables of `./vscode/c_cpp_properties.json` as following
```json
"env": {
        "xc8Path": "path-to-xc8-compiler", // ex C:/Program Files/Microchip/xc8/v2.32
        "chip": "chip-name" // ex pic16f877a
},
  ...
```

3. Update `nbproject/project.xml`  file

Specify your project name and add a creation UUID (i usually use [this website](https://www.guidgenerator.com/online-guid-generator.aspx) to generate UUIDs)
```xml
...
<data xmlns="http://www.netbeans.org/ns/make-project/1">
    <name>your-project-name</name>
    <!-- For example: a94829d3-c070-412e-a530-67c3846c4d5c-->
    <creation-uuid>your-project-creation-uuid</creation-uuid>
    <make-project-type>0</make-project-type>
    ...
```
4. Specify targeted device at `nbproject/configurations.xml` file

```xml
...
<toolsSet>
    <developmentServer>localhost</developmentServer>
    <!-- For example: PIC16F877A-->
    <targetDevice>your-targeted-device</targetDevice>
    <targetHeader></targetHeader>
    ...
```
5. Run `prjMakeFilesGenerator` on project directory

open a terminal at where prjMakefilesGenerator.bat located (typically `$inst_mplabx\mplab_platform\bin\prjMakefilesGenerator.bat` )

then run the following command
```bash
prjMakefilesGenerator "your-project-absoulute-path"
```

6. Compile the project

open terminal at your project directory and run `make`


