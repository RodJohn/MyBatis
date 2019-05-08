

# 找不到mapper

mybatis找不到mapper


## mapper的xml文件不在resource中



编译后的classes文件，发现其中确实只有class文件，并没有xml文件

查阅资料后，发现idea对目录结构里的存放的文件类型有要求，mapper文件必须放入到resources目录里，

但后期mapper文件变多后，会让resources目录里变得混乱起来

现在我就想让mapper文件放入到这里面，有什么解决方案呢？

在maven里加入resources内容，确保自己的mapper文件加入到编译的过程中，根据自己的情况更改一下


<build>
        <finalName>demo</finalName>
        <pluginManagement>
            <plugins>
           ......................
            </plugins>
        </pluginManagement>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                </includes>
                <filtering>true</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
    </build>
