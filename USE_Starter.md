

# 依赖

	dependencies {
	  compile group: 'org.mybatis', name: 'mybatis', version: '3.4.6'
	  compile group: 'mysql', name: 'mysql-connector-java', version: '6.0.6'
	}
	
	
# 项目结构


	src
		--java
	resource
		-- mybatis-config.xml
		-- mapper
			-- UserMapper.xml
	
	
	

# 配置

	<?xml version="1.0" encoding="UTF-8" ?>
	<!DOCTYPE configuration
			PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
			"http://mybatis.org/dtd/mybatis-3-config.dtd">
	<configuration>
		<environments default="development">
			<environment id="development">
				<transactionManager type="JDBC"/>
				<dataSource type="POOLED">
					<property name="driver" value="com.mysql.jdbc.Driver"/>
					<property name="url" value="jdbc:mysql://192.168.120.12:3306/test"/>
					<property name="username" value="dbuser"/>
					<property name="password" value="dbuser12345"/>
				</dataSource>
			</environment>
		</environments>
		<mappers>
			<mapper resource="mapper/UserMapper.xml"></mapper>
		</mappers>
	</configuration>

# 接口

	public interface UserMapper {

		User findById(Integer id);

	}


# mapper

	<?xml version="1.0" encoding="UTF-8" ?> <!DOCTYPE mapper
			PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
			"http://mybatis.org/dtd/mybatis-3-mapper.dtd">

	<mapper namespace="com.john.mybatis.dao.UserMapper">
		<select id="findById" parameterType="int" resultType="com.john.mybatis.model.User">
			select * from `user` where id = #{id}
		</select>
	</mapper>

# 测试

	public class Test {

		private static SqlSessionFactory sqlSessionFactory;
		private static Reader reader;

		static{
			try{
				reader    = Resources.getResourceAsReader("mybatis-config.xml");
				sqlSessionFactory = new SqlSessionFactoryBuilder().build(reader);
			}catch(Exception e){
				e.printStackTrace();
			}
		}

		public static SqlSessionFactory getSession(){
			return sqlSessionFactory;
		}

		public static void main(String[] args) {
			SqlSession session = sqlSessionFactory.openSession();
			try {
				UserMapper mapper = session.getMapper(UserMapper.class);
				User user = mapper.findById(1);
				System.out.println(user.getId());
				System.out.println(user.getName());
			} finally {
				session.close();
			}
		}
	}


