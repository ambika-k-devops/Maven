## Maven - Build Tool for JAVA Applications
---

```markdown
# Linux, Git and GitHub, Shell Scripting/Python

## Maven Build Tool

---

### Why You Need to Use?

➡️ **Developer → GitHub → Maven → Tomcat**

- **Build**: Build is a process of automating the packages (jar, war, ear)
- Maven is a popular build automation and project management tool used primarily for Java projects.
- Developed by the Apache Software Foundation.
- Maven is an open source build tool.
- Maven is platform independent.
- Maven is not an executable software (.exe). It is available as a `.zip` or `.tar.gz` (download and extract).
- To download Maven:  
  👉 [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)

---

### What Are the Build Tools?

#### Java
- Ant
- Maven
- Gradle

#### Python
- PyBuilder

#### .NET
- MS Build
- Nant

#### Ruby
- Rake

#### Go
- Go build tool

---

### What is JAR, WAR, EAR?

#### 1. Standalone Applications [JAR]
- Java code  
- JAR contains `.class` files

#### 2. Web Applications [WAR]
- JAVA code + Web content (HTML/CSS3/JS/images)  
- WAR contains: JAR + HTML/CSS3/JS/Images

#### 3. Enterprise Applications [EAR]
- JAVA code + Web content + standalone and web modules  
- EAR contains: JAR + WAR + HTML/CSS3/JS/Images + modules

➡️ [Download Maven](https://maven.apache.org/download.cgi)

---

### Maven Directory Structure

- `bin` → Contains binary files (`mvn`, etc.)
- `boot` → Contains jar files used at runtime
- `conf` → Configuration files (`settings.xml`)
- `lib` → Contains library files (jars)

---

### Default XML File Names for Build Scripts

| Tool   | Build Script            |
|--------|-------------------------|
| Maven  | `pom.xml`               |
| Ant    | `build.xml`             |
| Gradle | `build.gradle` (not XML)|

---

### Installation Commands (RHEL/CentOS based)

```bash
sudo yum install java -y     # Java 11 or 8
sudo yum install maven -y    # Maven 3.9.1
```

---

## Maven Installation

### System Requirements

- Maven 3.9+ requires JDK 8 or above
- No memory minimum requirement
- Disk: ~10MB for Maven installation
- OS: No strict requirement (scripts available for Unix & Windows)

**NOTE:** All external software is stored in `/opt` directory.

---

### Step-by-Step Installation

#### Step 1: Switch to root user

```bash
sudo su -
```

---

#### Step 2: Install Java

```bash
sudo su -
javac -version   # Check if Java compiler exists
```

**To search Java in Linux:**

```bash
sudo yum search java | grep OpenJDK
```

**To install JDK 1.8:**

```bash
sudo yum install java-1.8.0-openjdk-devel -y
```

**To install Java 11:**

```bash
sudo yum install java-11-openjdk-devel -y
```

---

#### Step 3: Install Maven

##### Pre-Requisite Software:
- Java (JDK) must be installed

```bash
javac -version
```

1. Login as root and change directory to `/opt`:

```bash
sudo su -
cd /opt/
yum install wget unzip -y
```

2. Download Maven:

```bash
wget https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.zip
unzip apache-maven-3.9.9-bin.zip
```

3. Set environment variables:

```bash
vi ~/.bash_profile
```

Add the following lines:

```bash
export M2_HOME=/opt/apache-maven-3.9.9
export PATH=$PATH:$M2_HOME/bin
```

To apply changes:

```bash
source ~/.bash_profile
```

To verify Maven:

```bash
mvn -version  # or mvn -v
```

---

## TL;DR

- **Maven** automates building and packaging Java projects into `.jar`, `.war`, or `.ear`.
- It is **platform-independent** and **requires Java (JDK)**.
- Install Java first, then Maven by downloading and extracting the ZIP, setting environment variables.
- Check everything with `mvn -version`.

---

## 🧠 Important Points to Remember

| Item                     | Detail                                                                 |
|--------------------------|------------------------------------------------------------------------|
| Maven Download URL       | [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi) |
| Required Java Version    | JDK 8 or JDK 11                                                        |
| Maven ZIP Location       | `/opt/` directory (custom install)                                     |
| Config File              | `~/.bash_profile` for setting `M2_HOME` and `PATH`                     |
| Build File for Maven     | `pom.xml`                                                              |
| Verify Maven             | `mvn -version` or `mvn -v`                                             |
| Maven Install Format     | ZIP (not `.exe`)                                                       |
| Directory Structure      | bin, boot, conf, lib                                                   |
| External Software Path   | `/opt`                                                                 |
| Shell Script to Apply Env| `source ~/.bash_profile`                                              |

---

```
