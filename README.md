# migrate-2-grails3
A Grails 2 plugin that performs a partial migration of a Grails 2 plugin or application to Grails 3

## Instructions

- Create an empty Grails 3 application or plugin (depending on what you're migrating) 
- Install this plugin in the application being migrating
- On the command-line set the current directory to the root of the project being migrated and run the following command

    grails migrate <path> <plugin package name>
    
### Arguments

- path: the *relative* path (from the application being migrated) to the empty Grails 3 application
- plugin package name: this argument is optional and only used if a plugin is being migrated. It specifies the package
name that will be used for the plugin descriptor's class. If omitted a package name of the form `grails.plugins.${appName}`
will be used 

## Automatic Migration Tasks

The plugin automatically performs the following tasks:

- copying Java/Groovy source files to the Grails 3 project
- copying unit/integration tests to the Grails 3 project
- copying the contents of `grails-app` and `web-app` to the Grails 3 project
 
## Manual Migration Tasks

There are a number of tasks involved in migrating to Grails 3 that the plugin does *not* perform, either because
it's impossible to automate them, or because automation of these tasks has not been completed yet. These are
described below

### Functional Tests

Any functional tests in your Grails 2 app (most likely in the `test/functional` directory) will not be copied into
the Grails 3 app. In Grails 3, functional test classes are stored under `src/integration-test/groovy`. [Support for
functional testing](https://grails.github.io/grails-doc/latest/guide/testing.html#functionalTesting) is added to
Grails 3, so any existing functional tests should be modified to use this support.

