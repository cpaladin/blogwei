---
title: Java String 的 hashCode
date: 2016-03-25 15:14:00

tags:
- Java
- String
- hashCode

categories:
- 个人笔记

---

  查看 `java.lang.String` 的 `hashCode()` 方法：
  
    public int hashCode() {
        int h = hash;
        if (h == 0 && value.length > 0) {
            char val[] = value;

            for (int i = 0; i < value.length; i++) {
                h = 31 * h + val[i];
            }
            hash = h;
        }
        return h;
    }
  代码比较简单，核心就是那个 for 循环，这个循环就是在计算 String 哈希码，计算公式为：val[0]\*31^(n-1) + val[1]\*31^(n-2) + ... + val[n-1]
  举个例子，String s = "abc", 那么哈希码为a\*31\*31 + b\*31 + c = 97\*31\*31 + 98\*31 + 99 = 96354
  
