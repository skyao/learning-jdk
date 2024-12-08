---
title: "列出候选"
linkTitle: "List"
weight: 10
date: 2024-07-18
description: >
  通过 list 命令列出可供选择的候选者列表
---

通过 `sdk list` 命令可以列出当前平台上可供选择的候选者列表：

```bash
sdk list
```

命令输出为：

```bash
================================================================================
Available Candidates
================================================================================
q-quit                                  /-search down
j-down                                  ?-search up
k-up                                    h-help

--------------------------------------------------------------------------------
Apache ActiveMQ (Classic) (5.17.1)                  https://activemq.apache.org/

Apache ActiveMQ® is a popular open source, multi-protocol, Java-based message
broker. It supports industry standard protocols so users get the benefits of
client choices across a broad range of languages and platforms. Connect from
clients written in JavaScript, C, C++, Python, .Net, and more. Integrate your
multi-platform applications using the ubiquitous AMQP protocol. Exchange
messages between your web applications using STOMP over websockets. Manage your
IoT devices using MQTT. Support your existing JMS infrastructure and beyond.
ActiveMQ offers the power and flexibility to support any messaging use-case.

                                                          $ sdk install activemq
--------------------------------------------------------------------------------
Ant (1.10.14)                                            https://ant.apache.org/

Apache Ant is a Java library and command-line tool whose mission is to drive
processes described in build files as targets and extension points dependent
upon each other. The main known usage of Ant is the build of Java applications.
Ant supplies a number of built-in tasks allowing to compile, assemble, test and
run Java applications. Ant can also be used effectively to build non Java
applications, for instance C or C++ applications. More generally, Ant can be
used to pilot any type of process which can be described in terms of targets and
tasks.

                                                               $ sdk install ant
......
```

会列出每一个支持的软件的名字/介绍和默认版本。

完整输出列表可以见 [list.txt](images/list.txt)

## 支持列表

看看 sdkman 具体支持哪些东东。

### Apache ActiveMQ

Apache ActiveMQ® is a popular open source, multi-protocol, Java-based message broker. It supports industry standard protocols so users get the benefits of client choices across a broad range of languages and platforms. Connect from clients written in JavaScript, C, C++, Python, .Net, and more. Integrate your multi-platform applications using the ubiquitous AMQP protocol. Exchange messages between your web applications using STOMP over websockets. Manage your IoT devices using MQTT. Support your existing JMS infrastructure and beyond.

ActiveMQ offers the power and flexibility to support any messaging use-case.

Apache ActiveMQ® 是一种流行的开源、多协议、基于 Java 的消息代理。它支持行业标准协议，因此用户可以从多种语言和平台的客户端选择中获益。可从 JavaScript、C、C++、Python、.Net 等语言编写的客户端进行连接。使用无处不在的 AMQP 协议集成您的多平台应用程序。通过 webockets 使用 STOMP 在网络应用程序之间交换信息。使用 MQTT 管理物联网设备。支持现有的JMS基础架构及更多。

ActiveMQ具有强大的功能和灵活性，可以支持任何消息传递使用情况。

### Ant

Apache Ant is a Java library and command-line tool whose mission is to drive processes described in build files as targets and extension points dependent upon each other. The main known usage of Ant is the build of Java applications.

Ant supplies a number of built-in tasks allowing to compile, assemble, test and run Java applications. Ant can also be used effectively to build non Java applications, for instance C or C++ applications. More generally, Ant can be used to pilot any type of process which can be described in terms of targets and tasks.

Apache Ant 是一个 Java 库和命令行工具，其任务是将构建文件中描述的进程作为相互依赖的目标和扩展点来驱动。Ant 的主要用途是构建 Java 应用程序。

Ant 提供了大量内置任务，允许编译、组装、测试和运行 Java 应用程序。Ant 还能有效地用于构建非 Java 应用程序，例如 C 或 C++ 应用程序。更广泛地说，Ant 可用于引导任何类型的进程，这些进程可以用目标和任务来描述。

### AsciidoctorJ

AsciidoctorJ is the official library for running Asciidoctor on the JVM. Using AsciidoctorJ, you can convert AsciiDoc content or analyze the structure of a parsed AsciiDoc document from Java and other JVM languages.

AsciidoctorJ 是在 JVM 上运行 Asciidoctor 的官方库。使用 AsciidoctorJ，你可以转换 AsciiDoc 内容或分析 Java 和其他 JVM 语言解析的 AsciiDoc 文档结构。

### Ballerina

Open source programming language and platform for cloud-era application programmers to easily write software that just works.

开源代码编程语言和平台，让云时代的应用程序员轻松编写能正常运行的软件。

### Bld

bld is a build system that allows you to write your build logic in pure Java.

bld was created because we're not really interested in build tools. We use them because we have to, but we'd rather just get on with coding the real stuff.

bld 是一个构建系统，允许您用纯 Java 编写构建逻辑。

之所以创建 bld，是因为我们对构建工具并不感兴趣。我们不得不使用它们，但我们更愿意继续编写真正的代码。

### Bpipe

Bpipe is a framework for running computational pipelines and workflows

Bpipe是一个运行计算管道和工作流的框架

### BTrace

BTrace is a safe, dynamic tracing tool for the Java platform. BTrace can be used to dynamically trace a running Java program (similar to DTrace for OpenSolaris applications and OS). BTrace dynamically instruments the classes of the target application to inject bytecode tracing code.

BTrace 是一款适用于 Java 平台的安全动态跟踪工具。BTrace 可用于动态跟踪运行中的 Java 程序（类似于 OpenSolaris 应用程序和操作系统的 DTrace）。BTrace 对目标应用程序的类进行动态检测，以注入字节码跟踪代码。

### Concurnas

Concurnas is an open source JVM programming language designed for building reliable, scalable, high performance concurrent, distributed and parallel systems.

Concurnas 是一种开源 JVM 编程语言，设计用于构建可靠、可扩展、高性能的并发、分布式和并行系统。

### ConnOR

ConnOR, short for ConnectOffsetReset, is a commandline tool for resetting Kafka Connect source connector offsets.

ConnOR 是 ConnectOffsetReset 的缩写，是重置 Kafka Connect 源连接器偏移量的命令行工具。

### Coursier

Coursier is the Scala application and artifact manager. It can install Scala applications and setup your Scala development environment. It can also download and cache artifacts from the web.

Coursier 是 Scala 应用程序和工件管理器。它可以安装 Scala 应用程序并设置 Scala 开发环境。它还能从网上下载和缓存工件。

### CUBA CLI

CUBA CLI is an open source command line utility that enables you to easily create projects based on CUBA Platform

CUBA CLI 是一款开源命令行工具，可让您轻松创建基于 CUBA Platform 的项目。

### CXF

Apache CXF is an open source services framework. CXF helps you build and develop services using frontend programming APIs, like JAX-WS and JAX-RS. These services can speak a variety of protocols such as SOAP, XML/HTTP, RESTful HTTP, or CORBA and work over a variety of transports such as HTTP, JMS or JBI.

Apache CXF 是一个开源服务框架。CXF 可帮助您使用 JAX-WS 和 JAX-RS 等前端编程 API 构建和开发服务。这些服务可以使用 SOAP、XML/HTTP、RESTful HTTP 或 CORBA 等多种协议，并通过 HTTP、JMS 或 JBI 等多种传输方式工作。

### Detekt

A static code analysis tool for the Kotlin programming language

用于 Kotlin 编程语言的静态代码分析工具

### docToolchain

docToolchain is an implementation of the docs-as-code approach for software architecture plus some additional automation. The basis of docToolchain is the philosophy that software documentation should be treated in the same way as code together with the arc42 template for software architecture.

docToolchain 是对软件架构 “文档即代码”（docs-as-code）方法的实现，并增加了一些自动化功能。docToolchain 的基础是软件文档应与代码一样处理的理念以及软件架构的 arc42 模板。

### Flink

Apache Flink is an open-source, unified stream-processing and batch-processing framework.It's a distributed processing engine for stateful computations over unbounded and bounded data streams.It has been designed to run in all common cluster environments, perform computations at in-memory speed and at any scale.

Apache Flink 是一个开源、统一的流处理和批处理框架。它是一个分布式处理引擎，用于在无界和有界数据流上进行有状态计算。它设计用于在所有常见的集群环境中运行，以内存中的速度和任何规模执行计算。

### Gaiden

Gaiden is a tool that makes it easy to create documentation with Markdown.

Gaiden是一个工具，可以轻松地使用Markdown创建文档。

### Graal Cloud Native 

Graal Cloud Native (GCN) is a curated set of Micronaut(tm) framework modules designed from the ground up to be compiled ahead-of-time with GraalVM Native image resulting in native executables ideal for microservices.With GCN, You can build portable cloud-native Java microservices that start instantly and use fewer resources to reduce compute costs.

Graal Cloud Native (GCN) 是一套经过精心设计的 Micronaut(tm) 框架模块，其设计初衷是通过 GraalVM Native 镜像进行提前编译，从而生成适用于微服务的本机可执行文件。

### Grace Framework 

Grace is a powerful open-source, One-Person web application Framework to help developers build Spring Boot applications rapidly using the Groovy programming language. Grace is a fork of Grails 5 that started development in early 2022.

Grace 是一个功能强大的开源单人 Web 应用程序框架，可帮助开发人员使用 Groovy 编程语言快速构建 Spring Boot 应用程序。Grace 是 Grails 5 的一个分叉，于 2022 年初开始开发。

### Gradle

Gradle is a build automation tool that builds upon the concepts of Apache Ant and Apache Maven and introduces a Groovy-based domain-specific language (DSL) instead of the more traditional XML form of declaring the project configuration.

Gradle uses a directed acyclic graph (DAG) to determine the order in which tasks can be run.

Gradle 是一款构建自动化工具，它以 Apache Ant 和 Apache Maven 的概念为基础，引入了基于 Groovy 的特定领域语言（DSL），而不是更传统的 XML 形式来声明项目配置。

Gradle 使用有向无环图（DAG）来决定任务的运行顺序。

### Gradle profiler

A tool for gathering profiling and benchmarking information for Gradle builds

用于收集Gradle构建的分析和基准测试信息的工具

### Grails

Grails is a powerful web framework, for the Java platform aimed at multiplying developers productivity thanks to a Convention-over-Configuration, sensible defaults and opinionated APIs. It integrates smoothly with the JVM, allowing you to be immediately productive whilst providing powerful features, including integrated ORM, Domain-Specific Languages, runtime and compile-time meta-programming and Asynchronous programming.

Grails 是一个功能强大的 Web 框架，适用于 Java 平台，旨在通过 “配置公约”、合理的默认设置和有主见的 API 来提高开发人员的工作效率。它能与 JVM 平滑集成，让您立即提高工作效率，同时提供强大的功能，包括集成的 ORM、特定域语言、运行时和编译时元编程以及异步编程。

### Groovy

Groovy is a powerful, optionally typed and dynamic language, with static-typing and static compilation capabilities, for the Java platform aimed at multiplying developers' productivity thanks to a concise, familiar and easy to learn syntax.

It integrates smoothly with any Java program, and immediately delivers to your application powerful features, including scripting capabilities, Domain-Specific Language authoring, runtime and compile-time meta-programming and functional programming.

Groovy 是一种功能强大、可选择类型的动态语言，具有静态类型和静态编译功能，适用于 Java 平台，旨在通过简洁、熟悉和易学的语法提高开发人员的工作效率。

它能与任何 Java 程序顺利集成，并能立即为您的应用程序提供强大的功能，包括脚本功能、特定域语言编写、运行时和编译时元编程以及函数式编程。

### GroovyServ

GroovyServ reduces startup time of the JVM for runnning Groovy significantly. It depends on your environments, but in most cases, it’s 10 to 20 times faster than regular Groovy.

GroovyServ 可大大缩短运行 Groovy 的 JVM 的启动时间。这取决于您的环境，但在大多数情况下，它比普通的 Groovy 快 10 到 20 倍。

### hadoop

Apache™ Hadoop® project develops open-source software for reliable, scalable, distributed computing.It's a framework that allows for the distributed processing of large data sets across clusters of computersusing simple programming models.It is designed to scale up from single servers to thousands of machines, each offering local computation and storage.

Apache™ Hadoop® 项目为可靠、可扩展的分布式计算开发开源软件。它是一个框架，允许使用简单的编程模型在计算机集群间分布式处理大型数据集。

### Helidon CLI

The Helidon CLI lets you easily create a Helidon project by picking from a set of archetypes. It also supports a developer loop that performs continuous compilation and application restart, so you can easily iterate over source code changes.

Helidon CLI 可让您从一系列原型中轻松创建 Helidon 项目。它还支持一个开发人员循环，可执行连续编译和应用程序重启，因此你可以轻松迭代源代码变更。

### http4k

http4k is the Functional toolkit for building HTTP applications in Kotlin

http4k是用于在 Kotlin 中构建HTTP应用程序的功能工具包

### Infrastructor

Infrastructor is an open source server provisioning tool written in Groovy

Infrastructor是一个用Groovy编写的开源服务器配置工具

### Jarviz

Jarviz is a JAR analyzer tool. You can obtaine metadata from a JAR such as its manifest, manifest entries, bytecode versions, declarative services, and more.

Jarviz 是一款 JAR 分析工具。你可以从 JAR 中获取元数据，如清单、清单条目、字节码版本、声明式服务等。

### Java

Java Platform, Standard Edition (or Java SE) is a widely used platform for development and deployment of portable code for desktop and server environments.

Java SE uses the object-oriented Java programming language. It is part of the Java software-platform family. Java SE defines a wide range of general-purpose APIs – such as Java APIs for the Java Class Library – and also includes the Java Language Specification and the Java Virtual Machine Specification.

Java 平台标准版（或 Java SE）是一个广泛使用的平台，用于开发和部署桌面和服务器环境的可移植代码。

Java SE 使用面向对象的 Java 编程语言。它是 Java 软件平台系列的一部分。Java SE 定义了大量通用 API（如 Java 类库的 Java API），还包括 Java 语言规范和 Java 虚拟机规范。

### JBake

JBake is a Java based, open source, static site/blog generator for developers and designers.

JBake 是一款基于 Java 的开源静态网站/博客生成器，适用于开发人员和设计人员。

### JBang

JBang makes it easy to use Java for scripting. It lets you use a single file for code and dependency management and allows you to run it directly.

JBang 可让您轻松使用 Java 编写脚本。它让您使用单一文件进行代码和依赖性管理，并允许您直接运行它。






