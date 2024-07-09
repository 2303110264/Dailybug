### Tomcat 10.0
#### WARNING: 웹 애플리케이션 []을(를) 위해, ObjectStreamClass$Caches로부터 soft references를 폐기하지 못했습니다.
#### java.lang.ClassCastException: class java.io.ObjectStreamClass$Caches$1 cannot be cast to class java.util.Map (java.io.ObjectStreamClass$Caches$1 and java.util.Map are in module java.base of loader 'bootstrap')
Server > tomcat v0.0 Server at ... > context.xml   
```xml
<Context>
...
  <!-- add this code -->
  <Resources cachingAllowed="true" cacheMaxSize="100000" />
  <!-- just one line -->
</Context>
```
---
### Mybatis 3.5.16
#### SEVERE: Context initialized 이벤트를 [org.springframework.web.context.ContextLoaderListener] 클래스의 인스턴스인 리스너에 전송하는 동안 예외 발생
#### org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'sqlSessionFactory' defined in ServletContext resource ...
이 에러가 최상단에 뜰 경우, 아래로 내려가면서 확인해야 한다.   
> Failed to parse mapping resource: '파일 경로'
> 당연하지만 '파일 경로'의 저 파일이 문제다.

...중괄호를 괄호로 닫아놓고 1시간동안 오류를 찾고 있었다.   

   ---   
1. Qoddi 가입방식 찾아보기   
2. dbcp 말고 org.postgresql.xa.PGXADataSource 써보기   
3. url+username+password만 써보기
4. <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">   
    <property name="driverClassName" value="org.postgresql.ds.PGSimpleDataSource"/>   
    <property name="url" value="jdbc:postgresql://localhost:5432/postgres"/>   
    <property name="username" value="postgres"/>   
    <property name="password" value="postgres"/>   
</bean>   
5. 문서 마저 세팅하고 사람 모으고 생각하기...
