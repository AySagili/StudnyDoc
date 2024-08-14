# 报错记录

Resolved [org.springframework.web.HttpMediaTypeNotAcceptableException: No acceptable representation]  
这个是在自己实现 getter 和 setter 方法后的报错，可能是 springboot 框架本身就是要使用规定的命名规则吧 用@Data 注解就解决了还有一种可能是用 set get 开头或许也可以
