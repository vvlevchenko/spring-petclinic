Docker: 
- build args: `JAVA_VERSION=21`
- run args: `-p 8080:8080 -m 10g`

WSL (ubuntu):
- install prerequisites:
```
sudo apt-get update -y
sudo apt-get install -qq -y unzip zip wget curl gdbserver libc6-dev libc6-dbg zlib1g-dev gcc openjdk-17-jre maven
curl -s "https://get.sdkman.io" | bash
source ~/.sdkman/bin/sdkman-init.sh
sdk install java graalce-21
```
- configure maven run configuration:
  - Run On `WSL - Ubunutu`
  - environment variables:
  `GRAALVM_HOME=~/.sdkman/candidates/java/21-graalce`
  - Run: `clean package`
  - Profiles: `native`
- configure `GraalVM Native Image`
  - Run On `WSL - Ubuntu`
  - Executable: `target/petclinic`
  - Symbol file: `target/petclinic.debug`

