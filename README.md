# learn-boot-step1
---

## 简介
这是用于 [MyBatis Generator](http://www.mybatis.org/generator/) 中生成注释这一步骤的自定义生成器，默认将数据库注释作为 Java 注释，并支持在生成的 Java 代码中附加注解

## 示例
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">
<generatorConfiguration>
    <properties resource="package/to/your/data_source.properties"/>
    <context id="context_mysql" defaultModelType="flat" targetRuntime="MyBatis3">
        <property name="javaFileEncoding" value="UTF-8"/>

        <!-- CommentWithAnnotationCommentGenerator -->
        <commentGenerator type="io.github.since1986.mybatis.comment.generator.CommentWithAnnotationCommentGenerator">
            <property name="fieldAnnotationFullyQualifiedNames" value="one.your.customer.FieldAnnotationClass,another.your.customer.FieldAnnotationClass"/>
            <property name="classAnnotationFullyQualifiedNames" value="one.your.customer.ClassAnnotationClass,another.your.customer.ClassAnnotationClass"/>
        </commentGenerator>

        <jdbcConnection driverClass="${driverClass}" connectionURL="${connectionURL}" userId="${userId}" password="${password}">
            <!-- better keep this -->
            <property name="useInformationSchema" value="true"/>
        </jdbcConnection>

        <javaModelGenerator targetPackage="your.model" targetProject="/path/to/your/project/src/main/java">
        </javaModelGenerator>


        <sqlMapGenerator targetPackage="your.mapper" targetProject="src/main/resources">
        </sqlMapGenerator>


        <javaClientGenerator targetPackage="your.mapper" type="ANNOTATEDMAPPER" targetProject="src/main/java">
        </javaClientGenerator>

        <table tableName="your_table" domainObjectName="YourDomain">
        </table>
    </context>
</generatorConfiguration>
```
