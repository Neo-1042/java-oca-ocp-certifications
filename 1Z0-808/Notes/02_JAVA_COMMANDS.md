# Compile, Run and Archive Java Files

Say we have the following on a Windows system:

First class:  
`C:\com\udemy\ocppackage\Ocp.java`

Second class:  
`C:\com\udemy\ocapackage\Oca.java`

Take the common-ground position:  
`cd C:\com\udemy`

## Compiling (`javac`)

```bash
javac ocppackage/Ocp.java ocapackage/Oca.java
# output: class files

# Compiling 2 whole packages with wildcards:
javac ocppackage/*.java ocapackage/*.java

# What if we want classes compiled to a specific directory?
javac -d classes ocppackage/Ocp.java ocapackage/Oca.java
# These *.classes will be inside the 'classes' folder
```

### Compiling with Dependencies

```bash
# -cp option can be used with the javac command to specify the
# location of the dependencies for the main program.
# i.e., your app depends on other files to run.
# Some of the files are in the package 'deps',
# and some are in myJar.jar:

# Windows locations (separated by ;)
javac -cp ".;C:\com\udemy\deps;C:\com\udemy\myJar.jar" myPackage.MyApp
# UNIX locations (separated by :)
javac -cp ".:/com/udemy/deps:/com/udemy/myJar.jar" myPackage.MyApp

# Using wildcards:
java -cp ".:/com/udemy/myjars/*" myPackage.MyApp
```

## Running (`java`)

```bash
# Omitting the ".class" part:
java ocppackage.Ocp

# After compiling into the 'classes' folder, we have 3 ways:
# cp = CLASSPATH
java -cp classes ocppackage.Ocp
java -classpath classes ocppackage.Ocp
java --class-path classes ocppackage.Ocp
```

# JAR = Java Archive files


```bash
# Create your own *.jar file from files in the current folder:
cd /com/udemy
# -cvf = create + verbose + file
# Verbose = the command line will provide more information
jar -cvf myNewJarFile.jar . # Mind the dot
jar --create --verbose --file myNewJarFile.jar .

# Create JAR from custom folder:
jar -cvf myNewJarFile.jar -C myFolder
```