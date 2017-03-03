# Caplin JTM Template

This project template provides a starting point for writing a Transformer 7 module using the Java Transformer Module (JTM) API [com.caplin.jtm](http://www.caplin.com/developer/api/transformer_java_sdk_2/latest).

> To create a Transformer 6 module, use the [Caplin Legacy JTM Template](https://github.com/caplin/project-templates/tree/master/jtm-legacy-template).

The project's build script, `gradle.build`, requires a local installation of [Gradle](https://gradle.org/). Alternatively, you can run the build commands using the provided Gradle Wrapper, `gradlew`. For more information on using a Gradle Wrapper, see [Executing a build with the Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html#using_wrapper_scripts) in the Gradle documentation.


## Getting started

Follow the instructions below to download and configure a JTM Template:

1. Download or clone the Caplin Project Templates repository.

1. In the `jtm-template/settings.gradle` file, change the value of the `rootProject.name` property to the name of your adapter project. The project name will be used as the name for the [service blade](http://www.caplin.com/developer/component/deployment-framework/features-and-concepts/cdf-blade-types#Service-blade).

1. In the `jtm-template/build.gradle` file, change the username and password to your Caplin credentials.

This project template does not include the libraries required to build the project. These libraries are downloaded when you build the adapter for the first time, or when you import the template directory to an IDE with Gradle support.


## Running your JTM during development
A Java Transformer Module (JTM) can be run only within Transformer's embedded JVM; it cannot be run within your IDE. To run and debug your JTM during development, deploy your JTM to the [Deployment Framework](http://www.caplin.com/developer/component/deployment-framework) (DFW) that hosts your Transformer, and then use remote debugging to monitor its execution.

**To setup remote debugging:**

1. In the Deployment Framework file `global_config/overrides/servers/Transformer/etc/java.conf`, set the configuration item `TRANSFORMER_JVM_DEBUGGER_PORT` to a valid port number.

    **Note**: if your Transformer is on a remote server, check that the server's firewall does not block the port number you assign to `TRANSFORMER_JVM_DEBUGGER_PORT`.

1. From the root of your DFW, run the command `./dfw start Transformer` to start (or restart) Transformer.

1. In your IDE, create a 'remote debugging' configuration for your project.

    * Set the host to Transformer's network address.

    * Set the port to the number you assigned to `TRANSFORMER_JVM_DEBUGGER_PORT`.

**To deploy your JTM:**

1. From the `project-templates/jtm-template` directory, run the command `gradle assemble`. This command packages your JTM within a new [service blade](http://www.caplin.com/developer/component/deployment-framework/features-and-concepts/cdf-blade-types#Service-blade) under the `build` directory.

1. Deploy the service blade to the DFW that hosts your Transformer. For instructions on how to deploy an adapter blade to a DFW, see [Deploy a custom blade](https://caplinportal.caplin.com/developer/component/deployment-framework/how-can-i/cdf-deploy-a-custom-blade).

    **Tip**: If you are deploying the service blade to a local DFW, then follow this tip to skip this step in future. Replace the JAR file <code><em>dfw-root</em>/active_blades/<em>your_module</em>/Transformer/lib/java/<em>your_module</em>.jar</code> with a symlink to the JAR file generated by Gradle in the `build/distributions` directory.

1. From the root of the DFW, run `./dfw start Transformer` to start (or restart) Transformer.

## Building and deploying the JTM's service blade

Follow the steps below to deploy your service blade:

1. From the `project-templates/jtm-template` directory, run the command `gradle assemble`. This command packages your JTM within a new [service blade](http://www.caplin.com/developer/component/deployment-framework/features-and-concepts/cdf-blade-types#Service-blade) under the `build` directory.

1. Deploy the service blade to each DFW in your deployment infrastructue. For instructions on how to deploy an adapter blade to a DFW, see [Deploy a custom blade](https://caplinportal.caplin.com/developer/component/deployment-framework/how-can-i/cdf-deploy-a-custom-blade).


## Issues
To report an issue with the template, please contact Caplin Support or [raise an issue](https://github.com/caplin/project-templates/issues) on GitHub.