---
title: Java String 的 intern
date: 2019-06-26 15:44:05

tags:
- Java
- String
- intern

categories:
- 学习笔记

---
  
    String s1 = new String("abc");
    String s2 = "abc";
    System.out.println(s1 == s2);  // false

    String s3 = new String("de") + new String("fg");
    s3.intern();
    String s4 = "defg";
    System.out.println(s3 == s4); // jdk1.6 false, jdk1.7 true
    
字符串常量池：
    jdk 1.6，在方法区中，属于永久代
    jdk 1.7，放在堆中
    jdk 1.8，取消了“永久代”，将常量池放在元空间，与堆独立
        
在jdk1.7后，执行intern()方法，会在常量池保存s3的引用，当定义s4时，发现"defg"已经存在，直接返回s3的引用，所以s3==s4。
    
    
    


  
