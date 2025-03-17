# project-1-maven-integration
### Step3: Install and Configure Maven in Jenkins Server

- We need to install MAVEN in Jenkins server. 

```sh
cd /opt
sudo wget https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz 
tar -xvzf apache-maven-3.9.6-bin.tar.gz
mv apache-maven-3.9.6 maven
```

- Next configure `M2_HOME` and `M2`(binary directory) environment variables and add them to the `PATH` so that we can run `maven` commands in any directory. You can search where is your JVM by using t`find / -name java-11*`

- Now you need to edit .bash_profile to add these variables to path and save 
```sh
M2_HOME=/opt/maven
M2=/opt/maven/bin
JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
PATH=$PATH:$HOME/bin:$M2_HOME:$M2:$JAVA_HOME
export PATH
```
- To apply the changes we have made to .bash_profile, either we can logout and log back in or run `source .bash_profile` command. It will upload the changes.

### Step4: Integrate Maven with Jenkins

- Now go to `Manage Jenkins` and `Global Tool Configuration` to add path fofr Java and Maven.

- We can configure a `Maven Project` to build our Code, go to `Dashboard` -> `NewItem`

```sh
Name = FirstMavenProject
Type: Maven Project
URL: https://github.com/nileshlip/hello-world-Projects.git
Root Pom: pom.xml
Goals and options: clean install
Save -> Build Now
```

- now we can go to `/var/lib/jenkins/workspace/FirstMavenProject/webapp/target` to see our build artifact webapp.war file.
