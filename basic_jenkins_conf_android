## Basic Jenkins Configuration for Android

Sdk configuration on the host
=====
- Install android sdk from https://developer.android.com/studio/index.html

> Bottom of the page, block *Get just the command line tools*


- unpack the sdk somewhere on the file system

> currently */Users/mac1/android_tooling/android-sdk-macosx*


- go to the sdk directly and update it by running the following command
```
$ *./tools/android update sdk --no-ui*
```

> this will download all the needed tools to build an android app

Jenkins configuration
====
- add the **ANDROID_HOME** environment variable to point where the android sdk is installed (in Jenkins, go to  Manage Jenkins, then Configure System, then add Env Variable)  

- install the following plugins:
  - xunit 
  - lint 
  - checkstyle

Jenkins Job configuration
====
- create a new jenkins project and configure it properly so that it can checkout the git repository (this means that their should be a dedicated jenkins user with rights access to the repository) 

- add a build step
  > select *Use Gradle Wrapper*
  check the *From Root Build Script Dir* 
  write down the gradle task(s) that should be ran
  in *Root Build script* fill in *lequipe* (this is because the app code is not at the root of the repository but it is inside *lequipe* directory

- add post build actions
  - publish xUnit test result report 
  - set the threshold as wanted and the proper pattern to indicate where xml test results can be found
  - to capture all test results from all modules: *rootDir/\*\*/build/test-results/\*\*/\*.xml* 

