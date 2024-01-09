# ORM框架（Object Relational Mapping
![img](https://img2023.cnblogs.com/blog/2342106/202304/2342106-20230419190431968-580784799.png)
一种为了解决面向对象与关系数据库存在的互不匹配的现象的技术

- 个人：
  - 就是有了orm框架内应用程序不在直接访问，数据库，而是通用持久化对象，（持久化对象有时通过orm框架内和关系性数据库的映射）得到
  - 将数据库数据转换为一对象

# 测试
```xml
<!--创建的xml需要引用的依赖-->
    <dependencies>
<!--        数据库连接依赖-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.30</version>
        </dependency>
<!--        用来测试，写测试类-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.2</version>
            <scope>test</scope>
        </dependency>

    </dependencies>
    <!-- ... -->
    <!-- 将src/main/java下的xml资源编译进clsses文件夹 -->
    <!-- 因为最终运行是target文件运行，如果不加那么在类路径下的配置文件就添加不进去 -->

     <build>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>true</filtering>
            </resource>
        </resources>
    </build>
```
依赖就是以前的lib，就是人间写好的api的jdk


# dp.properties
在resources下面
```properties
mysql.driver=com.mysql.cj.jdbc.Driver
mysql.url=jdbc:mysql://localhost:3306/mybatis?serverTimezone=UTC&characterEncoding=utf8&useUnicode=true&useSSL=false
mysql.username=root
mysql.password=root

```
# mybatis-config.xml
在resources下面
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!-- 环境配置 -->
    <!-- 加载类路径下的属性文件 -->
    <properties resource="db.properties"/>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <!-- 数据库连接相关配置 ,db.properties文件中的内容-->
            <dataSource type="POOLED">
                <property name="driver" value="${mysql.driver}"/>
                <property name="url" value="${mysql.url}"/>
                <property name="username" value="${mysql.username}"/>
                <property name="password" value="${mysql.password}"/>
            </dataSource>
        </environment>
    </environments>


</configuration>

```

# resource/Mapper/UserMapper.xml
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!-- 注意这是下面是mapper -->
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.itheima.pojo.User">
    <!--id ="接口中的方法名"parameterType="传入的参数类型"
　　resultType = "返回实体类对象，使用包.类名"-->
    <select id="findById" parameterType="int"
            resultType="com.itheima.pojo.User">
        select * from users where uid = #{id}
    </select>
</mapper>
```
这样创建了其实是查询不到的


# sql
`create database mybatis;`


# 测试方法
```java
public void userFindByIdTest() {
        //读取mybatis-config.xml内容
        String resources = "mybatis-config.xml"; Reader reader=null;
        try {
            reader= Resources.getResourceAsReader(resources);
        } catch (IOException e) {
            e.printStackTrace();
        }
//        初始化Mybatis数据库创建SqlSessionFactory类实例
        SqlSessionFactory sqlMapper=new SqlSessionFactoryBuilder().build(reader);
        SqlSession session=sqlMapper.openSession();
        User user=session.selectOne("findById",1);
        System.out.println(user.getUname());
        session.close();
    }
```
# mybatis流程图
![img](https://img2023.cnblogs.com/blog/2342106/202304/2342106-20230419191806216-252550275.png)