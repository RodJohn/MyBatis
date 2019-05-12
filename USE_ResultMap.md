
# 字段映射

	<resultMap id="userResultMap" type="User">
	<id property="id" column="user_id" />
	<result property="username" column="user_name"/>
	<result property="password" column="hashed_password"/>
	</resultMap>


