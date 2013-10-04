depends
=======

Ivy-based solution for publish and retrieval of artifacts to HTTP and/or file repository.

This project assumes Jenkins usage and Artifactory usage, and a very particular style of artifact resolution and publication.

However, with small changes, any build environment, and artifact server, could be made to work.

Environment
-----------
Java 1.7, Ant 1.9.2, Ivy 2.3.0

ant should be on your path. Ivy should be installed in the lib directory of Ant (all usual stuff)

Usage
-----
Best practice is to add this as a git submodule. 

Create a configuration file in *~/.ivy/ivysettings.properties*
```
artifact.server.host=artifactory.company.com
artifact.server.realm=Artifactory Realm 
artifact.server.username=admin
artifact.server.password=password
artifact.server.baseurl=https://artifactory.company.com/artifactory
my.org=com.company
```

### ivy.xml
In your project, it's assumed that there is a ivy.xml in the root of the project.

### Invoking Publication Script
In a build script, call ant like so:

```ant -f depends/publish.xml -Dproject.module=module-from-ivy-file```

### Invoking Retrieval Script
```ant -f depends/retrieve.xml```


Adding Depends as a Git Submodule
---------------------------------

There is nothing special about depends as a git submodule; this is just added as a convenience.
```
git submodule add git@github.com:sethcall/depends.git ./depends
git submodule update --init
git commit ./depends -m "Added submodule as ./depends"
```
