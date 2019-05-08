
# 动态SQL



# if

作用

	通过条件控制语句

注意

	字符串的null和空字符串
	<if test="name!=null and name.trim()!=''">

示例

	<select id="findActiveBlogWithTitleLike" resultType="Blog">
	  SELECT * FROM BLOG
	  WHERE state = ‘ACTIVE’
	  <if test="title != null">
		AND title like #{title}
	  </if>
	</select>
  
    
# choose when otherwise


# where

作用

	至少有一个语句成功时会去插入“WHERE”
	会去除语句的开头的“AND”或“OR”

示例

	<select id="findActiveBlogLike" resultType="Blog">
		SELECT * FROM BLOG
		<where>
		  <if test="state != null">
			  AND state = #{state}
		  </if>
		  <if test="title != null">
			  AND title like #{title}
		  </if>
		</where>
	</select>

# set

作用

	至少有一个语句成功时会去插入“SET”
	会去除语句的结尾的的“，”

示例

	<update id="updateAuthorIfNecessary">
	  update Author
		<set>
		  <if test="username != null">username=#{username},</if>
		  <if test="password != null">password=#{password},</if>
		  <if test="email != null">email=#{email},</if>
		</set>
	  where id=#{id}
	</update>


# trim


where

	<trim prefix="WHERE" prefixOverrides="AND |OR ">
	  ...
	</trim>

set

	<trim prefix="SET" suffixOverrides=",">
	  ...
	</trim>


# foreach

作用

	遍历集合
	
	当使用可迭代对象或者数组时，index 是当前迭代的次数，item 的值是本次迭代获取的元素。
	当使用 Map 对象，index 是键，item 是值。
	collection 为 list 代表集合  array代表数组
	
示例


	//接口方法
	ArrayList<User> selectByIds(List<Integer> ids);

	//xml映射文件
	<select id="selectByIds" resultMap="BaseResultMap">
	    Select * from jria where ID in
	    <foreach item="item" collection="list" open="(" separator="," close=")">
		  #{item}
	      </foreach>
	  </select> 
	
	
# 不够OOP

foreach 空集合

if的时候空对象 判断对象参数



