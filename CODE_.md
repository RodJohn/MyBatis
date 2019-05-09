

config
sqlsession
mapper
为什么接口可以调用方法
  

  sqlSession.getMapper
  代理的实现
  怎样生成代理对象
  




时序图

sqlsession


sqlSession作为manager 进行暴露行为

selecteOne   

execute

承担的功能太多，单一职责 

execute 模板模式

statementhandle

resultsethandle

关闭资源

errorcontant



mapperRegister 包装 xml 的语句 结果映射

mapperDate = sql + resultType 
