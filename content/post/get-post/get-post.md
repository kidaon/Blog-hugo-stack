---
title: spring
date: 2025-02-27
---
[Spring Quickstart](https://spring.io/quickstart)

### get method 获取params参数

```java
package com.example.demo.controller;  
  
  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RequestParam;  
import org.springframework.web.bind.annotation.RestController;  
import com.example.demo.pojo.ApiResponse;  
  
  
@RestController  
public class helloController { // 类名建议首字母大写  
  
    @RequestMapping("/hello")  
    public ApiResponse hello(@RequestParam("abc") String abc) {  
  
        return new ApiResponse(1000, "hello world" + abc, "success");  
    }  
}
```

....

### post method 获取参数

```java

```