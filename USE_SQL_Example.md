

# 概述

作用

	Example类指定如何构建一个动态的where子句
	Example类包含一个内部静态类 Criteria 包含一个用 anded 组合在where子句中的条件列表. 
	Example类包含一个 List 属性,所有内部类Criteria中的子句会用 ored组合在一起. 使用不同属性的 Criteria 类允许您生成无限类型的where子句.


# 示例

	CrmPostExample example = new CrmPostExample();
	CrmPostExample.Criteria criteria = example.createCriteria();
	criteria.andDepidEqualTo(depId);
	List<CrmPost> crmPosts = crmPostMapper.selectByExample(example);
