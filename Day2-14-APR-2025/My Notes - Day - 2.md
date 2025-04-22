# Maven Project & Lifecycle Notes

## Sample `pom.xml` [Project Object Model]
---

```markdown
```xml
<project>
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.jio</groupId>
    <artifactId>jio-project</artifactId>
    <version>1.0.0</version>
    <packaging>war</packaging>

    <name>Sample Project</name>
    <url>http://www.example.com</url>

    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- JUnit for unit testing -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/log4j/log4j -->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>1.2.17</version>
        </dependency>
    </dependencies>

    <profiles>
        <profile>
            <id>dev</id>
            <properties>
                <environment>development</environment>
            </properties>
        </profile>
        <profile>
            <id>prod</id>
            <properties>
                <environment>production</environment>
            </properties>
        </profile>
    </profiles>
</project>
```

---

## Testing Frameworks

| Language     | Framework |
|--------------|-----------|
| Java         | JUnit     |
| JavaScript   | Jest      |
| Python       | pytest    |
| C#           | NUnit     |
| Ruby         | RSpec     |
| C++          | gtest     |
| Go           | Testfy    |

---

## What is a Test Case?

- Test cases are written to **programmatically test source code**.
- Developed by **developers**, **not DevOps Engineers**.

### Example: JUnit Dependency

```xml
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
</dependency>
```

---

## 📌 IQ: From where are dependencies downloaded while running?

**Answer:** From the **central repository**.

---

## Maven Repositories

### 1. Maven Local Repository

- A directory on your machine where Maven stores downloaded artifacts.
- **Default locations:**
  - Linux: `~/.m2/repository`
  - Windows: `C:\Users\prasanth\.m2\repository`
  - Mac: `/users/prasanth/.m2/repository`

#### IQ: Is it possible to change the default location?

**Answer:** Yes.

#### Steps:

1. Open: `/conf/settings.xml`
2. Add:

```xml
<localRepository>/root/commonmavenrepo/</localRepository>
```

#### IQ: Why change the location?

**Answer:** To use a **common repository** for all developers, saving hard disk space.

---

### 2. Maven Central Repository

- Hosted by Maven community.
- Used if a dependency is **not** found in local repo.

📍 URL: [https://repo.maven.apache.org/maven2/](https://repo.maven.apache.org/maven2/)

---

### 3. Maven Remote Repository

- Examples: **Nexus**, **JFrog**

> In organizations, we store internal WAR files here instead of the public central repo.

📌 *Note: Detailed discussion in Nexus classes.*

---

## Maven Lifecycles

---

### 1. Clean Lifecycle

**Goals:**
- `pre-clean`
- `clean` → Deletes build history (e.g., `target/` directory)
- `post-clean`

✅ Command:  
```sh
mvn clean
```

---

### 2. Site Lifecycle

**Goals:**
- `pre-site`
- `site` → Generates documentation
- `post-site`
- `site-deploy` → Deploys to web server

✅ Command:  
```sh
mvn site
```

📌 Note: Developers often use **Swagger** instead of this lifecycle.

---

### 3. Default Lifecycle (Most Common)

| Phase     | Description |
|-----------|-------------|
| `validate` | Checks project structure & info |
| `compile`  | Compiles the source code |
| `test`     | Runs unit tests (e.g., JUnit) |
| `package`  | Packages code into JAR/WAR/EAR |
| `install`  | Installs package into local repo |
| `deploy`   | Deploys to remote repo |

✅ Example Commands:
```sh
mvn clean
mvn validate
mvn compile
mvn test
mvn package
mvn verify
mvn install
mvn deploy
```

---

### IQ: Can we pass two goals at once?

**Answer:** Yes  
**Example:**
```sh
mvn clean package
```

---

### IQ: How to skip unit test cases?

```sh
mvn clean package -DskipTests             # skips only tests
mvn clean package -Dmaven.test.skip=true  # skips tests and compilation
```

---

## LAB Instructions

### Step-by-Step

1. Clone the repo:  
   ```sh
   git clone <url>
   ```

2. Navigate to the directory.

3. Check contents:  
   ```sh
   tree
   ```

4. Run first time:  
   ```sh
   mvn clean package
   ```

5. Run again to verify dependency caching.

6. Check `target/` directory:
   - `classes/` → Compiled `.class` files
   - `test-classes/` → Unit test `.class` files

📌 **Note:** Run Maven commands where `pom.xml` is located.

7. Clean up:
   ```sh
   mvn clean
   ```

---

### How to Skip Running Unit Tests?

- Skip tests but keep compilation:  
  ```sh
  mvn clean package -DskipTests
  ```

- Skip both tests and compilation:  
  ```sh
  mvn clean package -Dmaven.test.skip=true
  ```

---
```
