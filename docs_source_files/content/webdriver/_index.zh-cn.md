---
title: "WebDriver"
chapter: true
weight: 5
---

# WebDriver

Selenium 最近最大的变化是包含了 WebDriver API。使用 Selenium 服务器以本地用户身份在本地或远程计算机上驱动浏览器，这标志着浏览器自动化方面的飞跃。

Selenium WebDriver 的角色与 RC 相同，并已合并了原始的 1.x 绑定。它既指语言绑定，也指单个浏览器控制代码的实现。通常将其称为 WebDriver 或有时称为 Selenium 2。

Selenium 1.0 + WebDriver = Selenium 2.0

* WebDriver 在更简单，更简洁的编程界面中进行了设计，同时解决了 Selenium-RC API 中的一些限制。

* 与 Selenium 1.0 相比，WebDriver 是一个紧凑的面向对象的 API。

* 它可以更有效地驱动浏览器，并克服了 Selenium 1 的局限性，这些局限性影响了我们的功能测试范围，例如文件上传或下载，弹出窗口和对话框障碍。

* WebDriver 克服了 Selenium RC 的 [单主机起源策略](//en.wikipedia.org/wiki/Same-origin_policy) 的局限性 。
