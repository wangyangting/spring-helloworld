# SpringMVC 错误集合

## 通配符的匹配很全面, 但无法找到元素 'mvc:annotation-driven' 的声明
一般这样的问题，即 **通配符的匹配很全面, 但无法找到元素 'xxx' 的声明**，
是由于在 xml 文件头引入的东西不对，或者不对称引起的。

报错前:
```
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:mvc="http://www.springframework.org/schema/tool"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/mvc
       http://www.springframework.org/schema/mvc/spring-mvc.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd">
```

修该后:
```
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/mvc
       http://www.springframework.org/schema/mvc/spring-mvc.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd">
```

报错前是用 idea 来生成的 .xml 文件，修该下就 OK 了

## java.lang.ArrayIndexOutOfBoundsException: 2925
jetty 错误片段如下

```java
java.lang.ArrayIndexOutOfBoundsException: 2925
```

将 pom.xml 中的依赖
```xml
<plugin>
  <groupId>org.mortbay.jetty</groupId>
  <artifactId>jetty-maven-plugin</artifactId>
  <version>8.1.16.v20140903</version>
</plugin>
```
修该成
```xml
<plugin>
  <groupId>org.eclipse.jetty</groupId>
  <artifactId>jetty-maven-plugin</artifactId>
  <version>9.4.11.v20180605</version>
</plugin>
```
即可。