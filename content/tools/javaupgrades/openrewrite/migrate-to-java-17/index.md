---
title: "迁移到Java17"
linkTitle: "迁移到Java17"
weight: 100
date: 2022-04-08
description: >
  迁移到Java17
---



https://docs.openrewrite.org/running-recipes/popular-recipe-guides/migrate-to-java-17



在本教程中，我们将使用 OpenRewrite 从 Java 8 自动迁移到 Java 17。将旧代码库升级到 Java 17 可能是一项艰巨而耗时的任务。作为开发人员，您可以使用 OpenRewrite 快速解决升级过程中遇到的最常见问题。

本配方涵盖以下主题：

- 使用任何 Java EE 规范的应用程序都将把这些依赖关系迁移到 Jakarta EE 8。此外，迁移到 Jakarta EE 8 还将为那些对 Jakarta EE API 有传递依赖关系的项目添加显式运行时依赖关系。目前，只支持基于 Maven 的构建文件。

- Java 早期版本中任何已废弃的 API（具有明确定义的迁移路径）都将自动应用到应用程序的源代码中。本秘诀中包含的补救措施最初是通过一个名为 Jdeprscan 的构建插件识别出来的。

- 当应用程序尝试使用未通过模块系统公开导出的 API 时，将记录非法反射访问警告。如果众所周知的第三方库提供了符合 Java 模块系统的版本，本教程将对其进行升级。

## 配置示例

在项目中加入 OpenRewrite 插件并依赖 rewrite-migrate-java，即可应用 Java 17 迁移配方：

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.openrewrite.maven</groupId>
      <artifactId>rewrite-maven-plugin</artifactId>
      <version>5.13.0</version>
      <configuration>
        <activeRecipes>
          <recipe>org.openrewrite.java.migrate.UpgradeToJava17</recipe>
        </activeRecipes>
      </configuration>
      <dependencies>
        <dependency>
          <groupId>org.openrewrite.recipe</groupId>
          <artifactId>rewrite-migrate-java</artifactId>
          <version>2.3.0</version>
        </dependency>
      </dependencies>
    </plugin>
  </plugins>
</build>
```

这时，你就可以运行 `mvn rewrite:run` 或 `gradlew rewriteRun` 来执行迁移了。运行迁移后，您可以使用 git diff（或类似工具）检查迁移结果，手动修复无法自动迁移的内容，然后提交迁移结果。

## 迁移前后

有关此配方所做更改的完整列表，请参阅 Java 11 和 Java 17 的参考页面。如果您有本项目尚未涵盖的特定用例，请联系我们的团队！
