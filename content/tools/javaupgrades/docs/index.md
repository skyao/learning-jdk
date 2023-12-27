---
title: "JavaUpgrades文档说明"
linkTitle: "文档"
weight: 20
date: 2022-04-08
description: >
  JavaUpgrades介绍
---



项目首页介绍

https://github.com/johanjanssen/JavaUpgrades

## Java 升级错误和解决方案示例

该项目展示了 Java 升级过程中遇到的错误以及必要的修复方法。

每个 Java 版本都有一个 Maven 模块，显示从该版本开始出错的地方以及如何修复。

本项目使用 Maven，但其他构建工具也会出现同样的问题。

本自述首先介绍了 Java 的一般问题和解决方案，然后介绍了每个特定 Java 版本的问题和解决方案。然后介绍在一台机器上运行多个 JDK 的各种方法。

最后一部分还介绍了如何运行示例。例如，Java 15 示例可以在 Java 14 上运行。在 Java 15 上运行时，损坏的示例会失败，而固定的示例会成功。

## 自动升级 Java

OpenRewrite 提供了各种自动升级应用程序甚至改进代码的方法。它会在本地进行修改，然后你可以决定是否要提交所有修改，或者是否要进行修改。与手动升级相比，使用 OpenRewrite 可以节省大量时间。

他们提供的一些秘诀：

- [迁移到 Java 17](https://docs.openrewrite.org/running-recipes/popular-recipe-guides/migrate-to-java-17)
- [从 JUnit 4 迁移到 JUnit 5](https://docs.openrewrite.org/running-recipes/popular-recipe-guides/migrate-from-junit-4-to-junit-5)

## Java 面临的普遍挑战

本文档描述了 Java 的较大变化。Java 还删除了许多（较小的）项目。本章列出了被移除的各种类别。有关详细信息，请查看发行说明：

Java 发行说明：

- [Java 10](https://www.oracle.com/java/technologies/javase/10-relnote-issues.html)
- [Java 11](https://www.oracle.com/java/technologies/javase/11-relnote-issues.html)
- [Java 12](https://www.oracle.com/java/technologies/javase/12-relnote-issues.html)
- [Java 13](https://www.oracle.com/java/technologies/javase/13-relnote-issues.html)
- [Java 14](https://www.oracle.com/java/technologies/javase/14-relnote-issues.html)
- [Java 15](https://www.oracle.com/java/technologies/javase/15-relnote-issues.html)
- [Java 16](https://www.oracle.com/java/technologies/javase/16-relnote-issues.html)
- [Java 17](https://www.oracle.com/java/technologies/javase/17-relnote-issues.html)

Security 路线图：

- [Oracle JRE and JDK Cryptographic Roadmap](https://java.com/en/jre-jdk-cryptoroadmap.html)

OpenJDK 特性：

- [Java 9](https://openjdk.java.net/projects/jdk9/)
- [Java 10](https://openjdk.java.net/projects/jdk/10/)
- [Java 11](https://openjdk.java.net/projects/jdk/11/)
- [Java 12](https://openjdk.java.net/projects/jdk/12/)
- [Java 13](https://openjdk.java.net/projects/jdk/13/)
- [Java 14](https://openjdk.java.net/projects/jdk/14/)
- [Java 15](https://openjdk.java.net/projects/jdk/15/)
- [Java 16](https://openjdk.java.net/projects/jdk/16/)
- [Java 17](https://openjdk.java.net/projects/jdk/17/)
- [Java 21](https://openjdk.java.net/projects/jdk/21/)

### 删除虚拟机标志/选项

例如

```java
-XX:+AggressiveOpts
```

和

```java
-Xoptimize
```

### 删除（根）证书

"The T-Systems Deutsche Telekom Root CA 2 certificate has expired and was removed from the cacerts keystore"

"T-Systems Deutsche Telekom Root CA 2 证书已过期，已从 cacerts 密钥库中删除"

### 删除加密算法

被认为不安全的算法已被删除。

### 删除垃圾回收器

例如，在 14 中删除了并发标记和清扫（CMS）垃圾收集器。

### 从 API 中移除

API 的部分内容（如方法）可能会被弃用，之后又会被移除。

您可以按 Java 版本查看 API 中已废弃和移除的部分。例如，通过 Java 版本年鉴 或 foojay

### 已删除的工具

有些工具已不再可用，有些工具（如 JDK Mission Control 和 JavaFX）现在可从不同供应商处以单独构建版的形式获得。

有些 JDK（如 ojdkbuild 和 Liberica JDK 的某些构建版）仍提供包含某些工具的 JDK。

## 各 Java 版本的问题和解决方案

### Java 11

#### JEP 320： 删除 Java EE 和 CORBA 模块

Java 11 中移除了 EE 包。如果您仍然需要它们，可以将它们添加为 Maven/Gradle 依赖项。

**请注意，您应使用新的 jakarta 软件包，因为旧软件包已不再更新。**

例如，JAXB 可以通过下面列出的依赖关系添加。不过，它已不再更新，最新版本是 2.3.0。

```xml
<dependency>
    <groupId>javax.xml.bind</groupId>
    <artifactId>jaxb-api</artifactId>
    <version>2.3.0</version>
</dependency>
```

相反，您应该使用 Jakarta 依赖项，它有更新的 3.0.0 版本:

```java
<dependency>
    <groupId>jakarta.xml.bind</groupId>
    <artifactId>jakarta.xml.bind-api</artifactId>
    <version>3.0.0</version>
</dependency>
```

#### 移除 javax.activation

错误示例

可在 java11/javaee_removed_broken 下找到示例代码

```java
package javax.activation does not exist
```

```java
cannot find symbol
[ERROR]   symbol:   class URLDataSource
```

解决方案

可在 java11/javaee_removed_fixed_new_package 下找到示例代码

添加必要的依赖项：

```java
<dependency>
    <groupId>com.sun.activation</groupId>
    <artifactId>jakarta.activation</artifactId>
    <version>2.0.1</version>
</dependency>
```

#### 移除 javax.annotation

错误示例
示例代码可在 java11/javaee_removed_broken 下找到。

```java
package javax.annotation does not exist
```

```java
cannot find symbol
[ERROR]   symbol:   class PostConstruct
```

解决方案
可在 java11/javaee_removed_fixed_new_package 下找到示例代码

添加必要的依赖项：

```xml
<dependency>
    <groupId>jakarta.annotation</groupId>
    <artifactId>jakarta.annotation-api</artifactId>
    <version>2.0.0</version>
</dependency>
```

#### 移除 javax.transaction

错误示例

可在 java11/javaee_removed_broken 下找到示例代码

```java
package javax.transaction does not exist
```

```java
cannot find symbol
[ERROR]   symbol:   class TransactionRequiredException
```

解决方案
可在 java11/javaee_removed_fixed_new_package 下找到示例代码

添加必要的依赖项：

```xml
<dependency>
    <groupId>jakarta.transaction</groupId>
    <artifactId>jakarta.transaction-api</artifactId>
    <version>2.0.0</version>
</dependency>
```

#### 移除 javax.xml.bind

示例错误

*示例代码可以在 java11/javaee_removed_broken 下找到*

```java
package javax.xml.bind.annotation does not exist
```

```bash
cannot find symbol
[ERROR]   symbol: class XmlRootElement
```

```bash
cannot find symbol
[ERROR]   symbol:   class JAXBException
```

解决方案

*示例代码可以在 java11/javaee_removed_fixed_new_package 下找到*

添加必要的依赖项：

对于 API，有：

```xml
<dependency>
    <groupId>jakarta.xml.bind</groupId>
    <artifactId>jakarta.xml.bind-api</artifactId>
    <version>3.0.0</version>
</dependency>
```

对于实现，下面列出了几个选项。如果您已经使用其中一个作为传递依赖项，那么最好使用该依赖项来避免冲突。

以下命令可用于检查是否已通过传递依赖项使用其中一个实现：

```bash
mvn dependency:tree -Dincludes=org.glassfish.jaxb:jaxb-runtime
mvn dependency:tree -Dincludes=com.sun.xml.bind:jaxb-impl
```

如果您没有 JAXB 实现作为传递依赖项，那么最好使用以下 Glassfish 实现。

```xml
<dependency>
    <groupId>org.glassfish.jaxb</groupId>
    <artifactId>jaxb-runtime</artifactId>
    <version>3.0.0</version>
    <scope>runtime</scope>
</dependency>
```

或者 jaxb-impl，它现在称为[旧 JAXB 运行时](https://mvnrepository.com/artifact/com.sun.xml.bind/jaxb-impl)

```xml
<dependency>
    <groupId>com.sun.xml.bind</groupId>
    <artifactId>jaxb-impl</artifactId>
    <version>3.0.0</version>
</dependency>
```

#### 删除 javax.jws javax.xml.soap javax.xml.ws

示例错误

*示例代码可以在 java11/javaee_removed_broken 下找到*

```java
package javax.xml.ws does not exist
```

```java
cannot find symbol
[ERROR]   symbol:   class Service
```

解决方案

*示例代码可以在 java11/javaee_removed_fixed_new_package 下找到*

添加必要的依赖项：

```xml
<dependency>
    <groupId>jakarta.xml.ws</groupId>
    <artifactId>jakarta.xml.ws-api</artifactId>
    <version>3.0.0</version>
</dependency>
<dependency>
    <groupId>com.sun.xml.ws</groupId>
    <artifactId>jaxws-rt</artifactId>
    <version>3.0.0</version>
</dependency>
```

#### 删除 Corba javax.activity javax.rmi.*

没有发布 Corba 的官方替换/依赖项

解决方案：

从 Corba 迁移或使用类似 glassfish-corba 的东西

#### 字体删除

JDK 包含一些字体，但在 Java 11 中删除了它们。如果应用程序使用了这些字体，而操作系统未提供这些字体，则会发生错误。

[来自 Azul](https://www.azul.com/the-font-of-all-knowledge-about-java-and-fonts/) 和 [AdoptOpenJDK](https://blog.adoptopenjdk.net/2021/01/prerequisites-for-font-support-in-adoptopenjdk/) 的详细信息

示例错误

*示例代码可以在 java11/removed_fonts 下找到*

```java
java.lang.UnsatisfiedLinkError: /usr/local/openjdk-11/lib/libfontmanager.so: 
  libfreetype.so.6: cannot open shared object file: No such file or director
```

```java
java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11FontManager
```

解决方案

*示例代码可在 DockerfileWithFonts 中找到*

安装必要的字体，例如：

```bash
apt install fontconfig
```

根据你的[方案](https://blog.adoptopenjdk.net/2021/01/prerequisites-for-font-support-in-adoptopenjdk/)，你可能需要添加一些额外的包，例如：libfreetype6 fontconfig fonts-dejavu。

一些 JDK 会自动安装所需的软件包。

#### JavaFX 删除

JavaFX 已从 JDK 中删除，并继续作为 OpenJFX。

一些供应商提供 OpenJFX 的构建，例如 [Gluon](https://gluonhq.com/products/javafx/)

一些供应商提供包含 OpenJFX 的 JDK 版本，例如 [Liberica 的完整版](https://bell-sw.com/pages/products/)和 [ojdkbuild](https://github.com/ojdkbuild/ojdkbuild/wiki/Motivation)

使用 [OpenJFX](https://openjfx.io/) 的 （Maven） 依赖项

#### Java Mission Control （JMC） 已删除

使用 JDK Mission control 的内部版本之一：

- [oracle](https://www.oracle.com/java/technologies/jdk-mission-control.html)
- [AdoptOpenJDK](https://adoptopenjdk.net/jmc.html)

### Java 15

#### JEP 372：删除 Nashorn JavaScript 引擎

Nashorn 不再包含在标准 JDK 中。

示例错误

*示例代码可以在 java15/nashorn_broken 下找到*

```bash
java.lang.NullPointerException: Cannot invoke "javax.script.ScriptEngine.eval(String)" because "engine" is null
```

解决方案

*示例代码可以在 java15/nashorn_fixed 下找到*

添加必要的依赖项：

```xml
<dependency>
    <groupId>org.openjdk.nashorn</groupId>
    <artifactId>nashorn-core</artifactId>
    <version>15.4</version>
</dependency>
```

### Java 16

#### JEP 396：默认情况下高度封装 JDK 内部结构

默认情况下，JDK 的内部结构不能再使用。这主要影响使用 JDK 低级功能的工具。

示例错误

*示例代码可以在 java16/lombok_broken 下找到*

```java
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.8.1:compile (default-compile) on project broken: Fatal error compiling: java.lang.IllegalAccessError: class lombok.javac.apt.LombokProcessor (in unnamed module @0x21bd20ee) cannot access class com.sun.tools.javac.processing.JavacProcessingEnvironment (in module jdk.compiler) because module jdk.compiler does not export com.sun.tools.javac.processing to unnamed module @0x21bd20ee -> [Help 1]
```

解决方案

*示例代码可以在 java16/lombok_fixed 下找到*

最好使用导致问题的依赖项的新版本。例如，Lombok 1.18.20 包括对 Java 16 的支持：

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.20</version>
    <scope>provided</scope>
</dependency>
```

如果没有新的依赖项可用，则可以打开 JDK 内部，以便可以使用它们。但是，这并不是最漂亮的解决方案：

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.8.1</version>
    <configuration>
        <fork>true</fork>
        <compilerArgs>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.comp=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.file=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.main=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.model=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.parser=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.tree=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.util=ALL-UNNAMED</arg>
            <arg>-J--add-opens=jdk.compiler/com.sun.tools.javac.jvm=ALL-UNNAMED</arg>
        </compilerArgs>
    </configuration>
</plugin>
```



### Java 17

#### Gradle

- 更新到 Gradle 7.3 以获得 Java 17 [支持](https://github.com/gradle/gradle/issues/16857)
- 更新到 Kotlin 1.6.0 以便能够将 jvmTarget 设置为 17

#### JEP 403：高度封装 JDK 内部

启动器选项 --illegal-access 不再适用于访问内部 JDK API。

#### 示例错误

```java
java.lang.reflect.InaccessibleObjectException: Unable to make … accessible: module java.base does not "opens …" to unnamed module …
```

解决方案

- 如果由依赖项触发，请升级依赖项
- 重构代码以不再使用内部 JDK API
- 作为最后的手段，例如：`--add-opens`

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <configuration>
        <argLine>
            --add-opens java.base/java.lang=ALL-UNNAMED --add-opens java.base/java.util=ALL-UNNAMED
        </argLine>
    </configuration>
</plugin>
```

#### JEP？

Mockito 在模拟使用值中方法的枚举时会引发异常，例如：

```java
public enum ExampleEnum {
    TEST {
        public String retrieve() {
            return "test";
        }
    };
}
```

```java
@ExtendWith(MockitoExtension.class)
public class ExampleEnumTest {

    @Mock
    private ExampleEnum exampleEnum;

    @Test
    public void testEnumWithMethods() {
        assertNotNull(exampleEnum);
    }
}
```

示例错误

*示例代码可以在 java17/mockito_fixed 下找到*

```java
org.mockito.exceptions.base.MockitoException:

Mockito cannot mock this class: class com.example.ExampleEnum.

If you're not sure why you're getting this error, please report to the mailing list.


Java               : 17
JVM vendor name    : Oracle Corporation
JVM vendor version : 17-ea+24-2164
JVM name           : OpenJDK 64-Bit Server VM
JVM version        : 17-ea+24-2164
JVM info           : mixed mode, sharing
OS name            : Linux
OS version         : 4.19.76-linuxkit


You are seeing this disclaimer because Mockito is configured to create inlined mocks.
You can learn about inline mocks and their limitations under item #39 of the Mockito class javadoc.

Underlying exception : org.mockito.exceptions.base.MockitoException: Could not modify all classes [class com.example.ExampleEnum, interface java.lang.constant.Constable, class java.lang.Object, interface java.lang.Comparable, interface java.io.Serializable, class java.lang.Enum]
Caused by: org.mockito.exceptions.base.MockitoException: Could not modify all classes [class com.example.ExampleEnum, interface java.lang.constant.Constable, class java.lang.Object, interface java.lang.Comparable, interface java.io.Serializable, class java.lang.Enum]
Caused by: java.lang.UnsupportedOperationException: class redefinition failed: attempted to change the class NestHost, NestMembers, Record, or PermittedSubclasses attribute
```

解决方案

尚不可用，请参阅 [Mockito GitHub](https://github.com/mockito/mockito/issues/2315) 存储库中的问题，其中提到了解决方法。

## Java 21

#### Bytebuddy

示例错误

通过 Bytebuddy 的 EqualsVerifier

```bash
-> Java 21 (65) is not supported by the current version of Byte Buddy which officially supports Java 20 (64) - update Byte Buddy or set net.bytebuddy.experimental as a VM property
```

解决方案

升级到支持 Java 21 的 Bytebuddy 版本或使用解决方法：

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <configuration>
        <argLine>-Dnet.bytebuddy.experimental=true</argLine><!-- Needed as EqualsVerifier uses Byte Buddy which doesn't support Java 21 -->
    </configuration>
</plugin>
```

### 所有 Java 版本

#### Unsupported class file major version 61 in JaCoCo

```bash
An error has occurred in JaCoCo Aggregate report generation. Error while creating report: Error while analyzing … Unsupported class file major version X
```

```
Execution default of goal org.pitest:pitest-maven:1.4.10:mutationCoverage failed: Unsupported class file major version 61 
```

```
Execution repackage of goal org.springframework.boot:spring-boot-maven-plugin:2.2.10.RELEASE:repackage failed: Unsupported class file major version 61
```

解决方案

类文件主要版本 61 用于 Java 17。确保您的插件/依赖项是最新的并支持 Java 17。

- 更新插件/依赖项

## 在一台计算机上运行多个 JDK

### 在运行示例之前设置JAVA_HOME

Maven 使用 `JAVA_HOME` 的值来选择 JDK。

显示当前`JAVA_HOME`

```bash
echo $JAVA_HOME
C:\Program Files\AdoptOpenJDK\jdk-16.0.0.36-hotspot
```

设置为另一个 JDK：`JAVA_HOME`

```bash
JAVA_HOME="[location of JDK]"
```

然后在其中一个 Java 目录（java11、java16...）中使用以下 Maven 命令来构建所有子模块，并在出现问题时继续：

```bash
mvn compile --fail-at-end -Dmaven.compiler.release=[Specify JDK version. Don't use this on Java 8 as it's not supported]
```

或者简短的版本：

```bash
mvn compile -fae -Dmaven.compiler.release=[Specify JDK version. Don't use this on Java 8 as it's not supported]
```

Java 8 的脚本版本

```bash
mvn compile -fae -Dmaven.compiler.target=8 -Dmaven.compiler.source=8
```

或者在 Maven 版本中更改：`pom.xml`

```xml
<properties>
    <maven.compiler.release>7</maven.compiler.release>
</properties>
```

### 使用 Docker 容器

然后在其中一个 Java 目录（java11、java16...）中使用以下 Docker 命令：

将JDK_VERSION更改为所需的任何版本（11 或更高版本）：

```bash
docker build -t javaupgrades -f ..\Dockerfile --build-arg DISABLE_CACHE="%date%-%time%" --build-arg JDK_VERSION=17 --progress=plain .
```

或者在 Java 8 上构建，这需要不同的配置：

```bash
docker build -t javaupgrades -f ..\DockerfileJava8 --build-arg DISABLE_CACHE="%date%-%time%" .
```

### Maven 工具链

Maven 工具链可用于配置计算机上存在的 JDK，然后选择一个用于项目的 JDK。`pom.xml`

首先创建一个位于 *${user.home}/.m2/*`toolchains.xml`

```xml
<?xml version="1.0" encoding="UTF8"?>
<toolchains>
    <toolchain>
        <type>jdk</type>
        <provides>
            <version>8</version>
        </provides>
        <configuration>
            <jdkHome>/path/to/jdk/8</jdkHome>
        </configuration>
    </toolchain>
    <toolchain>
        <type>jdk</type>
        <provides>
            <version>11</version>
        </provides>
        <configuration>
            <jdkHome>/path/to/jdk/11</jdkHome>
        </configuration>
    </toolchain>
    <toolchain>
        <type>jdk</type>
        <provides>
            <version>16</version>
        </provides>
        <configuration>
            <jdkHome>/path/to/jdk/16</jdkHome>
        </configuration>
    </toolchain>
    <toolchain>
        <type>jdk</type>
        <provides>
            <version>17</version>
        </provides>
        <configuration>
            <jdkHome>/path/to/jdk/16</jdkHome>
        </configuration>
    </toolchain>
</toolchains>
```

然后在 `pom.xml` 中配置要使用 `toolchains.xml` 中的哪个 JDK：

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-toolchains-plugin</artifactId>
            <version>3.0.0</version>
            <configuration>
                <toolchains>
                    <jdk>
                        <version>${maven.compiler.release}</version>
                    </jdk>
                </toolchains>
            </configuration>
            <executions>
                <execution>
                    <goals>
                        <goal>toolchain</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```



确保更新 Maven Compiler Plugin。当使用旧版本时，结合工具链插件，错误并不详细：

```bash
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.8.1:compile (default-compile) on project broken: Compilation failure -> [Help 1]
```

使用较新版本的 Maven 编译器插件时，错误消息提供了更详细的信息：

```bash
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.10.1:compile (default-compile) on project lombok_broken: Compilation failure
[ERROR] java.lang.IllegalAccessError: class lombok.javac.apt.LombokProcessor (in unnamed module @...) cannot access class com.sun.tools.javac.processing.JavacProcessingEnvironme
nt (in module jdk.compiler) because module jdk.compiler does not export com.sun.tools.javac.processing to unnamed module @...
```

## 有趣的其他事情

### 多发布 JAR

多版本 JAR 可以创建一个 JAR 文件，该文件支持多个 Java 版本以实现向后兼容性。

此示例使用在 Java 11 中引入的 `records` 和 `String.isBlank()`。该示例有两个主要目录：

- `src/main/java`: 用于 Java 17 以下的 Java 版本
- `src/main/java17`: 17及更高版本使用的

此示例的 JAR 文件应基于 Java 17 构建，然后可以在各种 Java 版本上使用。

以下命令可用于在 Java 17 上构建示例，然后在 8、11 和 17 上运行它们：

```bash
mvn package
run-multi-release-application.cmd
# docker build -t multi-release-jar --build-arg DISABLE_CACHE="%date%-%time%" --progress=plain .
```

确保所有 Java 版本的代码都包含相同的公共 API，否则可能会遇到运行时问题。IntelliJ 对此进行了检查，Java 17 现在[包含](https://github.com/openjdk/jdk/pull/3971)验证 JAR 文件的 `jar --validate` 选项。像 Maven 这样的构建工具不会自动验证它。
