

# #{ }

是预编译处理，
MyBatis在处理#{ }时，它会将sql中的#{ }替换为？，
然后调用PreparedStatement的set方法来赋值，
传入字符串后，会在值两边加上单引号，如上面的值 “4,44,514”就会变成“ '4,44,514' ”；

比如 

示例

	public User login( String userName, String password);

	<select id="login" resultType="com.zpc.mybatis.pojo.User">
		select * from tb_user where user_name = #{userName} and password = #{password}
	</select>




# ${ }
是字符串的拼接,， 
MyBatis在处理${ }时,它会将sql中的${ }替换为变量的值，传入的数据不会加两边加上单引号。

比如 列名 order by group by  表名

使用${ }会导致sql注入

示例


	public List<User> queryUserByTableName(String tableName);

	<select id="queryUserByTableName" resultType="com.zpc.mybatis.pojo.User">
	  select * from ${tableName}
	</select>

