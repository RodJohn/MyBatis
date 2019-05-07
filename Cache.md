

# 缓存



　　MyBatis 同样提供了一级缓存和二级缓存的支持

    一级缓存: 基于PerpetualCache 的 HashMap本地缓存，其存储作用域为 Session，当 Session flush 或 close 之后，该Session中的所有 Cache 就将清空。

　　2. 二级缓存与一级缓存其机制相同，默认也是采用 PerpetualCache，HashMap存储，不同在于其存储作用域为 Mapper(Namespace)，并且可自定义存储源，如 Ehcache。

　　3. 对于缓存数据更新机制，当某一个作用域(一级缓存Session/二级缓存Namespaces)的进行了 C/U/D 操作后，默认该作用域下所有 select 中的缓存将被clear。
  
  
# 一级缓存

## 特点

开关

	一级缓存默认是开启的，并且一直无法关闭

缓存命中

	1、同一个session中
	2、相同的SQL和参数


缓存清除

	sqlSession.clearCache();可以强制清除缓存

	update、insert、delete的时候，会清空缓存

## 示例


# 二级缓存

## 特点

mybatis 的二级缓存的作用域是一个mapper的namespace ，同一个namespace中查询sql可以从缓存中命中。

## 缺点





