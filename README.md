# TB-specific gradle plugin made after the work by Xyarilty
# gradle-treasureboat-plugin
## Building WebObjects / TreasureBoat applications with Gradle


gradle-treasureboat-plugin is a Gradle helper plugin to build WebObjects / [Project treasureboat](http://www.wocommunity.org) based applications. It provides basic facilities to accomodate the specific project structure and requirements of WO applications and helps deploying them in a test environment.

## basic usage

Check out the plugin and run `gradle build publishToMavenLocal` to publish into your local maven repository. Then add a buildscript dependency on the plugin, use either the `TBApplication` or `TBFramework` plugin and further configure the plugin in the `treasureboat` block.

	buildscript {
		repositories {
			mavenLocal()
			mavenCentral()
		}

		dependencies {
			classpath 'org.treasureboat.gradle:gradle-treasureboat-plugin:1.0.0'
		}
	}

	version = '1.2.3'

	apply plugin: 'TBApplication'

	treasureboat {
		tbVersion = '6.1.2'
		webobjectsVersion = '5.4.3'
		applicationClass = 'er.movies.Application'

		deploymentServers = ['localhost']
		deploymentSSHUser = 'wouser'
		deploymentPath = '/home/wouser/apps'
		deploymentSSHPort = 2222
		deploymentMonitorBounceTasks = ['localhost':'Movies']
		deploymentSSHIgnoreHostKey = true
	}


## supplied tasks

**TBFramework** - build a WO framework in build/project.framework

**TBApplication** - build a WO application in build/project.woa

**copyDependencies** - copy all dependent JARs and frameworks into the build folder

**copyToServers** - copy the resulting .woa to configured deployment servers

**copyToServer-<servername>** - copy the resulting .woa to one configured deployment server

**deployToServers** - set the application binary path and bounce the application on the configured JavaMonitors

**deployToServer-<servername>/<applicationName>** - set the application binary path on one JavaMonitor/application and bounce

## License

See LICENSE, forks and pull requests are welcome.
=======
# tb-gradle-plugin
