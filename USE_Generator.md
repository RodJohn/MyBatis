
# 概述

作用

	Mybatis-Generator可以从数据库读取数据按需生成Model、dao、xml
	
注意

	每次生成都会覆盖掉以前的结果，建议建立专门的Generator项目
	

# 配置文件


示例

	<?xml version="1.0" encoding="UTF-8"?>
	<!DOCTYPE generatorConfiguration
			PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
			"mybatis-generator-config_1_0.dtd">

	<generatorConfiguration>
		<classPathEntry location="my-generator\src\main\resources\mybatis\mysql-connector-java-5.1.8.jar"/>

		<context id="MysqlTables" targetRuntime="MyBatis3">
			<!--去除注释  -->
			<commentGenerator>
				<property name="suppressAllComments" value="true"/>
			</commentGenerator>

			<jdbcConnection driverClass="com.mysql.jdbc.Driver"
							connectionURL="jdbc:mysql://localhost:3306/test"
							userId="root"
							password="123456">
			</jdbcConnection>

			<javaTypeResolver>
				<property name="forceBigDecimals" value="false"/>
			</javaTypeResolver>

			<javaModelGenerator targetPackage="com.test.dal.dao" targetProject="my-generator\src\main\java">
				<property name="enableSubPackages" value="true"/>
				<property name="trimStrings" value="true"/>
			</javaModelGenerator>

			<sqlMapGenerator targetPackage="xml" targetProject="my-generator\src\main\resources">
				<property name="enableSubPackages" value="true"/>
			</sqlMapGenerator>

			<javaClientGenerator type="XMLMAPPER" targetPackage="com.test.dal.dao" targetProject="my-generator\src\main\java">
				<property name="enableSubPackages" value="true"/>
			</javaClientGenerator>

			<table schema="gp" tableName="test2" domainObjectName="Test2">
				<property name="useActualColumnNames" value="false"/>
				<columnOverride column="DATE_FIELD" property="startDate"/>
				<ignoreColumn column="FRED"/>
				<columnOverride column="LONG_VARCHAR_FIELD" jdbcType="VARCHAR"/>
			</table>

		</context>
	</generatorConfiguration>

常用参数

    classPathEntry 数据库驱动jar的位置
    jdbcConnection 连接信息、用户名、密码
    targetPackage  输出路径
    table          定义各个表的信息
	


# 使用方法

	mybatis-generator有三种用法：命令行、eclipse插件、maven插件

## gradle

说明

	虽然mybatis generator没有提供gradle的插件，
	但gradle可以调用ant任务，因此，gradle也能启动Mybatis Generator。

参考

	https://segmentfault.com/a/1190000013534059
	https://chenkaihua.com/2015/12/19/running-mybatis-generator-with-gradle/

## maven

项目结构

	

添加依赖

		<build>
			<plugins>
				<plugin>
					<groupId>org.mybatis.generator</groupId>
					<artifactId>mybatis-generator-maven-plugin</artifactId>
					<version>1.3.3</version>
					<configuration>
						<configurationFile>${project.basedir}/src/main/resources/mybatis/generatorConfig.xml</configurationFile>
					</configuration>
				</plugin>
			</plugins>
		</build>

运行

	mybatis-generator:generate  -e
