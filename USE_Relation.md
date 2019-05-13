
# 关联

  关联查询和懒加载

# association

## 说明

association

## 示例

要求

	查询指定文章并携带作者信息
	
结果类

	public class ArticleWithAuthor extends Article  {
		private Author author;
	}
	
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
	

语句

	<select id="selectArticleById" resultMap="ArticleWithAuthorResultMap" >
		select * from article where id=#{id} 
	</select>


ResultMap

	<resultMap id="ArticleWithAuthorResultMap" type="ArticleWithAuthor" extends="ArticleResultMap">
	   <association property="author" column="id"                       
				select="test.mybatis.dao.articleMapper.selectArticleById" />
	</resultMap>
	
	
	<resultMap id="ArticleResultMap" type="Article" >
		<id property="id" column="id"/>
		<result property="name" column="name"/>
		<result property="context" column="context"/>
		<result property="authorId" column="authorId"/>
	</resultMap>

	<select id="selectArticleById" resultMap="ArticleResultMap" >
		select * from article where id=#{id} 
	</select>

# collection 

## 说明

association

## 示例

要求

	查询指定作者及其所有文章
	
结果类

	public class AuthorWithArticle extends Author  {
		private List<Article> articles;
	}
语句

	<select id="selectAuthorById" resultMap="AuthorWithArticleResultMap" >
		select * from author where id=#{id} 
	</select>

ResultMap

	<resultMap id="AuthorWithArticleResultMap" type="AuthorWithArticle" extends="AuthorResultMap">
	   <collection  property="author" column="id"                       
				select="test.mybatis.dao.articleMapper.selectArticleByUserId" />
	</resultMap>

	<resultMap id="AuthorResultMap" type="Author" >
		<id property="id" column="id"/>
		<result property="name" column="name"/>
	</resultMap>
	
