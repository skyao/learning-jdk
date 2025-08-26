---
title: "Rewrite介绍"
linkTitle: "介绍"
weight: 100
date: 2022-04-08
description: >
  OpenRewrite支持大规模分布式源代码重构，用于框架迁移、漏洞补丁和API迁移。
---

https://docs.openrewrite.org/

## **大规模自动化源代码重构**

OpenRewrite支持大规模分布式源代码重构，用于框架迁移、漏洞补丁和API迁移。虽然最初的重点是 Java 语言，但 OpenRewrite 一直在[扩大语言和框架的覆盖范围]().

## 语义代码搜索和转换

OpenRewrite 项目是一个[语义代码搜索](https://en.wikipedia.org/wiki/Semantic_search)以及 Java 和其他源代码的转换生态系统。它由一个预打包的重构配方平台组成，用于常见的框架迁移和风格一致性任务。它还允许您定义自定义配方以实现广泛的源代码转换。

## OpenRewrite 有什么作用？

OpenRewrite 的工作原理是对[无损语义树]()（LST） 表示您的源代码，并将修改后的树打印回源代码。然后，您可以查看代码中的更改并提交。对 LST 的修改在[游客]()和访客被聚合成配方(recepes). OpenRewrite 配方对遵循原始格式的源代码进行微创更改。

例如，如果要在所有测试文件中一致地使用静态导入，而不是手动执行此操作，则可以使用 `OpenRewrite 提供的 UseStaticImport` 访问器。应用于下面的文件，您可以看到这生成的更改。

```java
// Before OpenRewrite
import org.junit.Assert;
...

Assert.assertTrue(condition);
```



```java
// After OpenRewrite
import static org.junit.Assert.assertTrue;
...

assertTrue(condition);
```



## 后续步骤

- 如果您想了解如何使用 OpenRewrite 在 Maven 或 Gradle 项目中执行代码转换，请查看 [设置项目和运行配方指南](https://docs.openrewrite.org/running-recipes/getting-started).
- 如果您想学习如何创建自己的食谱，请从[配方开发环境指南]() 开始，然后完成[编写 Java 重构配方指南]().
