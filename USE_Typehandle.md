

太麻烦了 
要么全局  要么一个一个SQL标签上去写


https://blog.csdn.net/u012702547/article/details/54572679




# 枚举

    Mybatis 可以映射枚举类，对应的实现类为 EnumTypeHandler 或 EnumOrdinalTypeHandler 。

    EnumTypeHandler ，基于 Enum.name 属性( String )。默认。
    EnumOrdinalTypeHandler ，基于 Enum.ordinal 属性( int )
    都不是我们想要的
