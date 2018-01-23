QTMGradlePlugin uploads result file(s) generated in a Gradle project to QTM Enterprise server.
The plugin, if used in a gradle project, provides an additional gradle task 'publishResultsToQTM'

To use the plugin,
'gradle clean install' - to install the plugin in your local maven repository. 
Use the plugin from anywhere in your gradle project, by including the following code in 'build.gradle' file...

apply plugin: 'com.icpl.qtmgradleplugin'

qtmConfig 
{
	qtmUrl = 'https://qtmserverurl.com/'
	qtmAutomationApiKey = 'xjdkghrghdhejdt...'
	automationFramework = 'JUNIT'
	testSuiteName = 'QTM4Gradle Test Run - JUNIT'
	testResultFilePath = '/test-results/test/'
	platformName = 'MyPlatform2'
	buildName = 'myCycleName'
}

buildscript
{
    repositories 
	{
        mavenLocal()
		mavenCentral()
    }
    dependencies 
	{
        classpath 'com.icpl:QTMGradlePlugin:1.1'
    }
}

use command 'gradle test publishReslutsToQTM' from your project.

...or alternatively, use the executable jar file (generated by command 'gradle clean build') directly as a dependency in your Gradle project 'build.gradle' file.

The task publishResultsToQTM always looks for qtmConfig in build.gradle file of your project. Provide following details :-

qtmUrl - url to qtm instance
qtmAutomationApiKey - Automation Key
automationFramework - JUNIT/TESTNG/CUCUMBER/QAS
testSuiteName (optional) - name of test suite.
buildName - Name of cycle linked to test suite
testResultFilePath - path to result file (or directory for multiple files) relative to build directory
platformName(optional) - Name of the platform to connect the suite