### 在XML中配置SQL语句

```xml
<mapper namespace="entity.Monkey">
    <select id="selectMonkey" resultType="entity.Monkey">
      select * from monkey where id = #{id}
    </select>
</mapper>
```

上面就是一个最简单的配置它有以下部分组成

- 标签：也就是 <select> <update> <insert> <delete> 这四种
- id：因为我们后面要在代码中引用它，所以肯定要给它一个唯一标识符
- resultType：我们要把查询到的记录和Java中的实体对应，肯定要告知MyBatis返回的记录对应哪个实体了
- SQL语句：没什么好说的，就是核心
- SQL参数：动态的参数是SQL语句的基本需求，我们在调用的时候传递进去就行了



然后我们注意，如果参数是简单类型，很好办，直接传递就行了。比如上面的SQL语句，我们在代码中可以这样传递参数

```java
Monkey monkey = session.selectOne("selectMonkey", 1);
```



而对于对象类型，

