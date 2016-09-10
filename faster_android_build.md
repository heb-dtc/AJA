# AndroidStudio on leash

- use oracle JDK instead of the openJDK  
install the *oracleJDK* anywhere on your system  
define an env. variable called *STUDIO_JDK* referencing where the *oracleJDK* is installed  
`$ export STUDIO_JDK=<path-to-jdk-root-dir>`

- use latest version of gradle. this can be forced in the root build.gradle file  
```
task wrapper(type: Wrapper) {
    gradleVersion = 'X.X'
}
```  
- Enable incremental dex build. Again add to the build.gradle of your main app module  
```
dexOptions {
        incremental true
}
```  
- use custom gradle properties to restrain the amount of RAM Android studio/gradle can use  
in the gradle.properties file of your project or the global one for your system it is possible to   
configure the Java process that will be used to execute your build.  
The following have proven themselves useful  
```
org.gradle.daemon=true
org.gradle.parallel=true
org.gradle.configureondemand=true
org.gradle.workers.max=<some-number>
org.gradle.jvmargs=-Xms256m -Xmx1024M
Xms -> initial amount of memory to be used
Xmx -> max amount of memory to use
amount should be given with a unit (k, m, g)
```
