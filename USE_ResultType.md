# resultType

作用

	使用resultType定义返回值类型
	可以让ResultSet中的结果设置到和列名一致的java属性中
		
示例

	package com.someapp.model;
	public class User {
	  private int id;
	  private String username;
	  private String hashedPassword;
	}
	
	<select id="selectUsers" resultType="com.someapp.model.User">
		select id, username, hashedPassword from some_table where id = #{id}
	</select>

# 类型别名

作用

	使用别名代替类的完全限定名称，会更简便

示例

	<!-- mybatis-config.xml 中 -->
	<typeAlias type="com.someapp.model.User" alias="User"/>

	<!-- SQL 映射 XML 中 -->
	<select id="selectUsers" resultType="User">
		select id, username, hashedPassword from some_table where id = #{id}
	</select>
	


# 类名和属性名不一致

开启驼峰转换

	开启自动驼峰命名规则（camel case）映射，
	即从经典数据库列名 A_COLUMN 到经典 Java 属性名 aColumn 的类似映射。 	
	<settings>
	  <setting name="mapUnderscoreToCamelCase" value="true"/>
	</settings>
	
在SQL中转换

	<select id="selectUsers" resultType="User">
	  select
		user_id             as "id",
		user_name           as "userName",
		hashed_password     as "hashedPassword"
	  from some_table
	  where id = #{id}
	</select>

使用ResultMap

	
	
