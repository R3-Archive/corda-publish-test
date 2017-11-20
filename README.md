# Corda Publish Test

## Purpose

This project is intended to test whether Corda has published successfully to Artifactory or the public JCenter/Maven repos

This is a separate project from the main Corda build so that a) developers are never blocked by unrelated publishing
processes, b) to avoid any sort of interference between gradle builds that may make the test invalid.

## Usage

To test Artifactory (doesn't test JCenter or Maven Central):

    ./gradlew --refresh-dependencies clean build
    
To test JCenter (without Artifactory):

    ./gradlew --refresh-dependencies -Pcorda.disableArtifactory clean build
    
## Limitations 

Corda requires JCenter and mavenCentral to always be specified due to relying on dependencies in those repositories, 
and Gradle does not provide a way to force specific dependencies to use specific repositories. 
See [this issue](https://github.com/gradle/gradle/issues/1369).