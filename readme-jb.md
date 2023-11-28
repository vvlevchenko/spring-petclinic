## Notes
this is petclinic working with h2, so no additional container required for db
# Build
## Container
Container at the moment based on Dockerfile and based on public community GraalVm images, if you like use Enterprise images
please consult with [Oracle* Enterprise Repository Documentation](https://docs.oracle.com/en/graalvm/enterprise/22/docs/getting-started/container-images/#get-started-with-graalvm-enterprise-container-images).
It's recommended to create maven and gradle repositories on host to avoid unwanted full project rebuild on each compilation 
(e.g. $HOME/m2_docker and $HOME/gradle_docker) and mount them to run/build container run configuration

# Maven
To build with maven it's required to create maven configuration with our Dockerfile target (don't forget to point `JAVA_VERSION` in build args, by default 21 is used).
It's strongly recommended to add something like `-v $USER_HOME$/m2_docker:/root/.m2` in `Run Target/Run Options` to avoid full rebuild on each build operation.

# Gradle
It's addional mount point in container configuration e.g `-v $PROJECT_DIR$:/project` in `Run Target/Run Options`
To build with gradle it's required to create `Pre Launch` configuration in your new `GraalVM Native Image` configuration and use `Run Extenal Tool`.
Here please add  (`+`) tool: `Program`: `./gradlew`, `Arguments`: `bootBuildImage`, `Working Directory`: accordingly `/project`

# Run/Debug
For debug used the same container. To configure run configuration please create `GraalVM Native Image` run configuration with target.
- Executable:  `$PROJECT_DIR$/target/petclinic`
- Symbol File:  `$PROJECT_DIR$/target/petclinic.debug`

