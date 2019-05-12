# 参数传递

	从接口的参数列表往XML传递参数
	一般使用注解传参和Bean传参法
 
# 顺序传参

接口

	public User selectUser(String name, int deptId);
	
XML

	<select id="selectUser" resultMap="UserResultMap">
		select * from user
		where user_name = #{0} and dept_id = #{1}
	</select>

说明

	#{}里面的数字代表你传入参数的顺序。
	一旦顺序调整容易出错。

# 注解传参

接口

	public User selectUser(@Param("userName") String name, int @Param("deptId") deptId);

XML

	<select id="selectUser" resultMap="UserResultMap">
		select * from user
		where user_name = #{userName} and dept_id = #{deptId}
	</select>

说明

	#{}里面的名称对应的是注解@Param括号里面修饰的名称。
	
	
# Map传参

接口

	public User selectUser(Map<String, Object> params);

XML

	<select id="selectUser" parameterType="java.util.Map" resultMap="UserResultMap">
		select * from user
		where user_name = #{userName} and dept_id = #{deptId}
	</select>

说明

	#{}里面的名称对应的是Map里面的key名称。
	这种方法适合传递多个参数，且参数易变能灵活传递的情况。
	如果传递参数中没有对应的key值，在执行sql语句时默认取的是null

# Bean传参

接口

	public User selectUser(User user);

XML

	<select id="selectUser" parameterType="com.test.User" resultMap="UserResultMap">
		select * from user
		where user_name = #{userName} and dept_id = #{deptId}
	</select>
说明

	#{}里面的名称对应的是User类里面的成员属性。
	

# 集合传参

	参考动态SQL中foreach

	
