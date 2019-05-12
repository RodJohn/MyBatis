

# #

原理

	MyBatis在处理#{ }时，它会将sql中的#{ }替换为？，
	调用PreparedStatement的set方法来赋值，
	传入字符串后，会在值两边加上单引号，
	如 “4,44,514”就会变成“ '4,44,514' ”；

示例

	public User login( String userName, String password);

	<select id="login" resultType="com.zpc.mybatis.pojo.User">
		select * from tb_user where user_name = #{userName} and password = #{password}
	</select>




# $

原理

	对于$的赋值MyBatis 不会修改或转义字符串

适用于

	列名，表名

示例


	public List<User> queryUserByTableName(String tableName);

	<select id="queryUserByTableName" resultType="com.zpc.mybatis.pojo.User">
	  select * from ${tableName}
	</select>

