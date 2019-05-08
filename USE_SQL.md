

# select

## 作用

	select标签用于定义一个查询语句	

## 示例

	<select id="selectPersons" resultType="hashmap">
	  SELECT * FROM PERSON 
	</select>
	
	
## 功能要点
	
	id
		当前名称空间下的statement的唯一标识
	resultType
		将结果集映射为java的对象类型。必须（和 resultMap 二选一）
	resultMap
		将结果集映射为java的自定义类型

# update and delete

作用

	update、delete标签用于定义一个修改语句	

示例

	<delete id="deleteAuthor">
	  delete from Author where id = 1
	</delete>

	
属性
	
	id返回修改行数



# insert

作用

	insert标签用于定义一个修改语句	

示例

	<insert id="insertAuthor" >
	  insert into Author  values ("john")
	</insert>

	
属性
	
	id返回修改行数

useGeneratedKeys:开启主键回写
keyColumn：指定数据库的主键
keyProperty：主键对应的pojo属性名

	
# sql

作用

	sql标签用于定义一个可被引用的语句	

示例	
	
	<sql id="userColumns"> id,username,password </sql>

	<select id="selectUsers" resultType="map">
	  select <include refid="userColumns"></include>
	  from some_table 
	</select>	
	
 
