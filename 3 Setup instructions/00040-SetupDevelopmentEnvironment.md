## Setup Oskari development environment

This section describes how to setup development environment for Oskari using source code. If you want to customize Oskari, this is the correct section.

For setting up an instance using the ready Jetty bundle see [Setup Jetty](00030-SetupJetty.md)

### Requirements

The following items are required for the development process:

* JDK 8
* [Maven 3+](http://maven.apache.org/) (developed using 3.5.0)
* [Git client](http://git-scm.com/) (git is mandatory for contributing any changes to Oskari) - Optionally download zip file from [oskari-server GitHub repo](https://github.com/oskariorg/oskari-server)
* `{jetty.base}` refers to the oskari-server folder in an unzipped [Jetty bundle](/download)

### Setup Git configuration

Configure line endings: [https://help.github.com/articles/dealing-with-line-endings/](https://help.github.com/articles/dealing-with-line-endings/)

Ignore file permissions:

	git config --global core.fileMode false

### Fetch Oskari-server source code

With command line git:

    git clone https://github.com/oskariorg/oskari-server.git

Or download the codes in zip format from [GitHub](https://github.com/oskariorg/oskari-server).

Additional Maven modules can be contributed outside git though if they are compatible with the current develop/master branch, but this is not advised.

Note! The sample application, including its source code and build, is available in `{jetty.base}/sample-application` within the [Jetty bundle](/download). The Jetty bundle uses the pre-built code located in the `dist` folder. To update the sample application you can replace the contents of the `sample-application` folder with a clone from https://github.com/oskariorg/sample-application, and build the application following the instructions in its README.md file.

### Build Oskari server

Build all modules that Oskari server is composed of with the following command:

    cd oskari-server
    mvn clean install

### Fetch sample-server-extension source code and compile it

To test your changes on a running web app you can use [sample-server-extension](https://github.com/oskariorg/sample-server-extension/) to create a web app using your modified version of oskari-server.

Check that the oskari.version in pom.xml matches the project version of oskari-server you built.

Download and install the sample-server-extension with the following commands:

    git clone https://github.com/oskariorg/sample-server-extension.git
    cd sample-server-extension
    mvn clean install

### Copy updated/relevant artifacts under `{jetty.base}/webapps`

Map functionality: sample-server-extension/webapp-map/target/oskari-map.war
