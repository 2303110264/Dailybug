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
