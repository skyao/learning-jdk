---
title: "在不修改构建的情况下在 Maven 项目上运行 Rewrite"
linkTitle: "在 Maven 项目上运行 Rewrite"
weight: 300
date: 2022-04-08
description: >
  在不修改构建的情况下在 Maven 项目上运行 Rewrite
---



https://docs.openrewrite.org/running-recipes/running-rewrite-on-a-maven-project-without-modifying-the-build



在本教程中，我们将应用 Rewrite [recipe](https://docs.openrewrite.org/concepts-and-explanations/recipes)  （配方）添加到使用 Maven 构建的源代码存储库中，而无需修改构建本身。根据配方是否具有配置参数，此说明略有不同。请注意，您需要先安装 [Maven](https://maven.apache.org/download.cgi) 以运行 shell 命令。

## 在没有配置参数的情况下运行配方

如果您尝试运行的配方没有任何必需的配置参数，则可以通过执行 shell 命令来运行配方。

> 我们 [recipe 文档](https://docs.openrewrite.org/reference/recipes) 包括针对任何没有配置参数的配方运行的特定 shell 命令。您可能会发现复制并运行提供的命令比手动创建它更容易。

如果配方来自[core Rewrite库](https://github.com/openrewrite/rewrite)（如[删除未使用的导入](https://docs.openrewrite.org/reference/recipes/java/removeunusedimports)），然后您可以运行以下命令并将 `org.openrewrite.java.RemoveUnusedImports` 替换为要运行的配方的路径：

```bash
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.activeRecipes=org.openrewrite.java.RemoveUnusedImports
```

如果配方来自不同的库（例如[迁移到 Jakarta EE 9](https://docs.openrewrite.org/reference/recipes/java/migrate/jakarta/javaxmigrationtojakarta)），然后您可以运行以下命令并将 `org.openrewrite.recipe：rewrite-migrate-java：LATEST` 替换为配方的工件，并将 `org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta` 替换为要运行的配方的路径：

```bash
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:LATEST \
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.jakarta.JavaxMigrationToJakarta
```



## 使用配置参数运行配方

如果您尝试运行的配方具有配置参数，则需要：

1. [ 在项目根目录中创建或更新 `rewrite.yml` 文件](https://docs.openrewrite.org/running-recipes/getting-started#step-5-run-a-recipe-with-yaml-configuration).在那里，您需要创建一个新配方，该配方包装要运行的配方并指定要使用的参数。

2. 运行一个 shell 命令，该命令执行您在步骤 1 中定义的新配方。

例如，如果你想运行 [ChangePackage 配方](https://docs.openrewrite.org/reference/recipes/java/changepackage) 若要将 `org.old.package.name`  更改为 `org.new.package.name`，需要创建一个`如下所示的 rewrite.yml` 文件：

```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.NameYouDefine
recipeList:
  - org.openrewrite.java.ChangePackage:
      oldPackageName: org.old.package.name
      newPackageName: org.new.package.name
```

然后，您可以通过执行以下 shell 命令来运行该配方：

```bash
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.activeRecipes=com.yourorg.NameYouDefine
```

