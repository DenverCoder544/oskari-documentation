## Setup Oskari development environment

This document describes how to setup development environment for Oskari using source code. If you want to develop / maintain oskari yourself this is the correct section.
For setting up an instance using the ready jetty bundle check out [Setup Jetty](00030-SetupJetty.md)

### Requirements

The following items are assumed installed.

* JDK 8
* [Maven 3+](http://maven.apache.org/) (developed using 3.5.0)
* Git client (http://git-scm.com/) - Optionally download zip file from https://github.com/oskariorg/oskari-server
* `{jetty.base}` refers to the oskari-server folder in an unzipped [Jetty bundle](/download)

### Setup Git configuration

Configure line endings: [https://help.github.com/articles/dealing-with-line-endings/](https://help.github.com/articles/dealing-with-line-endings/)

Ignore file permissions:

	git config --global core.fileMode false

### Fetch Oskari-server source code

With commandline git:

    git clone https://github.com/oskariorg/oskari-server.git

Note! You can also download the codes in zip format from Github, but for contributing any changes to Oskari git is mandatory.
Additional Maven modules can be contributed outside git though if they are compatible with the current develop/master branch, but this is not adviced.

Note! The sample application, including its source code and build, is available in `{jetty.base}/sample-application` within the [Jetty bundle](/download). The Jetty bundle uses the pre-built code located in the `dist` folder. To update the sample application you can replace the contents of the `sample-application` folder with a clone from https://github.com/oskariorg/sample-application, and build the application following the instructions in its README.md file.

### Build Oskari server

This will build all modules that Oskari server is composed of.

    cd oskari-server
    mvn clean install

### Fetch sample-server-extension source code and compile it

To test your changes on a running web app you can use sample-server-extension to create a webapp using your modified version of oskari-server.
Check that the oskari.version in pom.xml matches the project version of oskari-server you built.

    git clone https://github.com/oskariorg/sample-server-extension.git
    cd sample-server-extension
    mvn clean install

### Copy updated/relevant artifacts under `{jetty.base}/webapps`

Map functionality: sample-server-extension/webapp-map/target/oskari-map.war
