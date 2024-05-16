# Labo01 - Environment Setup

* [Labo description](https://cpnv-es-ngy.gitbook.io/vir1/labs/labo01-environment-setup)

## DevOps Stack to setup

Mention in this documentation the orders carried out and the results obtained.

If you have opted for a graphical installation, provide screenshots and describe the procedure up to the result obtained.

### Cloud cmd line interface - AWS Cli

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

```bash
➜  ~ aws --v  
aws-cli/2.15.41 Python/3.11.8 Linux/6.5.0-28-generic exe/x86_64.linuxmint.21 prompt/off

```

### IDE - Intellij

First, install jetbrains-toolbox.

Once done, launch jetbrains-toolbox and install Intellij Ultimate (2024.1).

### Containers Engins - Docker

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$UBUNTU_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### Versioning - Git + Git flow

```
sudo apt install git git-flow
```

Result:

```bash
➜  ~ git --version
git version 2.34.1
➜  ~ git flow version
1.12.3 (AVH Edition)
```

### IDE Plugin - Docker plugin for IntelliJ

Launch Intellij and go to File -> Settings -> Plugins -> Marketplace and search for "Docker", then install the plugin.

### Development Kit - JDK

```bash
curl https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.deb 
```

Double-click on the downloaded file to start installation.

Once installation is complete, check the Java version installed.

```bash
➜  ~ java --version
```

If the Java version is not 17.0.11, change the default version:

```bash
sudo update-java-alternatives -s /usr/lib/jvm/jdk-17-oracle-x64
```

### Package manager - Maven

``` bash
cd /tmp; wget https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz
```

``` bash
tar xf apache-maven-3.9.6-bin.tar.gz
```

``` bash
sudo mv apache-maven-3.9.6 /opt/maven
```

``` bash
sudo chown -R root:root /opt/maven
```

``` bash
sudo su
```

``` bash
cat <<EOF >> /etc/profile.d/mymavenvars.sh
export JAVA_HOME=/usr/lib/jvm/default-java
export M2_HOME=/opt/maven
export MAVEN_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
EOF
ln -s /opt/maven/bin/mvn /usr/bin/mvn
```

``` bash
chmod 755 /etc/profile.d/mymavenvars.sh
```

``` bash
source /etc/profile.d/mymavenvars.sh
```

``` bash
➜  ~ mvn --version
Apache Maven 3.9.6 (bc0240f3c744dd6b6ec2920b3cd08dcc295161ae)
Maven home: /opt/maven
Java version: 17.0.11, vendor: Oracle Corporation, runtime: /usr/lib/jvm/jdk-17-oracle-x64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "6.5.0-28-generic", arch: "amd64", family: "unix"
```

## Schema

https://www.figma.com/file/IQ2lvgJiNUcMiOnzDSlltX/Untitled?type=design&node-id=0%3A1&mode=design&t=ouoVib8HBWRkv5Md-1

## Analysis

Answer the questions below, giving reasons for your answer (link, source).

### AWS CLI

* How does the AWS Cli interact with the cloud ?

```
il communique avec l'api d'AWS pour envoyer des commandes et recevoir des réponses
```

* What other ways do we have of dialoguing/interacting with the AWS cloud if we wanted to do without the CLI?

```
soit via la console web, soit via des SDK
```

* What commands do I need to run in the CLI to start an ec2 instance?

```
aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids sg-903004f8 --subnet-id subnet-6e7f829e
```

### Docker Engine

* What type of hypervisor does Docker use?

```
Docker is a platform for developing, shipping, and running applications. It uses containerization technology to package and isolate applications with their entire runtime environment, including dependencies, into a single container that can be run on any Linux or Windows server. 
```

* What role does the Docker Desktop play in the Docker architecture?

```
a faciliter l'accès au Docker Engine.
```

### Java Environment

* JDK, JRE, JVM... what's the difference?

```
JDK: Java Development Kit, contient le JRE et les outils de développement

JRE: Java Runtime Environment, contient la JVM et les librairies nécessaires pour exécuter des applications Java

JVM: Java Virtual Machine, machine virtuelle qui exécute le bytecode Java
```

### Maven

* What is the command you need to use Maven to retrieve dependencies (and only that)?

```

```


