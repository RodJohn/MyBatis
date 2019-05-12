
# select

作用

	select标签用于定义一个查询语句	
	
常用参数
	
	id
		当前名称空间下的statement的唯一标识
	statementType 	
		设定语句类型 默认值：PREPARED。
	resultType
		将结果集映射为java的对象类型。
		如果返回的是集合，那应该设置为集合包含的类型，而不是集合本身
	resultMap
		将结果集映射为java的自定义类型
		（和 resultMap 二选一）

示例

	<select id="selectPersons" resultType="com.john.User">
	  SELECT * FROM User 
	</select>


# update 

作用

	update标签用于定义一个修改语句	

示例

	<delete id="deleteAuthor">
	  delete from Author where id = 1
	</delete>

返回修改行数

	要获取返回修改行数
	直接在mapper接口文件直接返回int类型即可
	sql语句和正常一样，无需设置返回值类型
	mybatis框架会自动完整这些功能
	（JDBC链接中可能需要参数useAffectedRows=true）

# delete

	主要用法类似于update	

# insert

	主要用法类似于update
	下面演示主键的生成和设置
	
## useGeneratedKeys

说明

	使用数据库自动生成主键的字段并设置到目标属性上
	
参数

	useGeneratedKeys 	
		MyBatis 使用 JDBC 的 getGeneratedKeys 方法来取出由数据库内部生成的主键，默认值：false。
	keyProperty 	
		MyBatis 会通过 getGeneratedKeys 的返回值或者通过 insert 语句的 selectKey 子元素设置它的键值，

示例

	<insert id="insertAuthor" useGeneratedKeys="true" keyProperty="id">
	  insert into Author values (#{username},#{password},#{email},#{bio})
	</insert>

## selectKey

说明

	使用自定义SQL生成的数据设置为主键，并设置到目标属性上
	
参数


示例

	<insert id="insertAuthor">
	  <selectKey keyProperty="id" resultType="int" order="BEFORE">
		select MAX(id)+1 a from User
	  </selectKey>
	  insert into User  values (#{id}, #{username}, #{password})
	</insert>



	
# sql

作用

	sql标签用于定义一个可被引用的语句	

示例	
	
	<sql id="userColumns"> id,username,password </sql>

	<select id="selectUsers" resultType="map">
	  select <include refid="userColumns"></include>
	  from some_table 
	</select>	
	
	
