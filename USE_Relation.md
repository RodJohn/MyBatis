
# 关联

  关联查询和懒加载


# association

https://www.cnblogs.com/yansum/p/5819973.html


public class Article {
    private Integer id;
    private String name;
    private String context;
    private Integer authorId;
}

public class Author {
    private Integer id;
    private String name;
}

<select id="selectArticleById" resultMap="ArticleResultMap" >
	select * from article where id=#{id} 
</select>

<select id="selectAuthorById" resultMap="AuthorResultMap" >
	select * from author where id=#{id} 
</select>



<resultMap id="ArticleResultMap" type="Article" >
    <id property="id" column="id"/>
    <result property="name" column="name"/>
	<result property="context" column="context"/>
    <result property="authorId" column="authorId"/>
</resultMap>

<resultMap id="AuthorResultMap" type="Author" >
    <id property="id" column="id"/>
    <result property="name" column="name"/>
</resultMap>


要求

	查询指定文章并携带作者信息
	
结果类

	public class ArticleWithAuthor extends Article  {
		private Author author;
	}

ResultMap

<resultMap id="ArticleWithAuthorResultMap" type="ArticleWithAuthor" extends="ArticleResultMap">
    <result property="level1" column="LEVEL1"/>
    <result property="level2" column="LEVEL2"/>
</resultMap>

<resultMap id="articleResultMap" type="test.mybatis.entity.Article">
  <id column="id" property="id" jdbcType="VARCHAR" javaType="java.lang.String"/>
  <result column="articleTitle" property="articleTitle" jdbcType="VARCHAR" javaType="java.lang.String"/>
 <result column="articleContent" property="articleContent" jdbcType="VARCHAR" javaType="java.lang.String"/>
 </resultMap>
  （当然，这里还有查询user表的语句，省略）	
