---
title: "定位元素"
weight: 3
---

{{% notice info %}}
<i class="fas fa-language"></i> 页面需要从英语翻译为简体中文。
您熟悉英语与简体中文吗？帮助我们翻译它，通过 pull requests 给我们！
{{% /notice %}}

### 定位单个元素

使用 WebDriver 时要学习的最基本的技术之一是如何查找页面中的元素。WebDriver 提供了许多内置的选择器类型，其中一个选择器类型是通过它的 ID 属性来查找的:

{{< code-tab >}}
  {{< code-panel language="java" >}}
WebElement cheese = driver.findElement(By.id("cheese"));
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
driver.find_element_by_id("cheese")
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
IWebElement element = driver.FindElement(By.Id("cheese"));
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
driver.find_element(id: "cheese")
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
const cheese = await driver.findElement(By.id('cheese'));
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
val cheese: WebElement = driver.findElement(By.id("cheese"))
  {{< / code-panel >}}
{{< / code-tab >}}

如示例所示，在 `WebDriver` 实例对象上定位 WebDriver 中的元素。`findElement(By)` 方法返回另一个基本对象类型 `WebElement`。

* `WebDriver` 代表了浏览器
* `WebElement` 表示特定的 DOM 节点
  （控件，例如链接或输入字段等）

一旦你有了一个“已找到”的 Web 元素引用，就可以通过对该对象实例使用相同的调用来缩小搜索范围：

{{< code-tab >}}
  {{< code-panel language="java" >}}
WebElement cheese = driver.findElement(By.id("cheese"));
WebElement cheddar = cheese.findElement(By.id("cheddar"));
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
cheese = driver.find_element_by_id("cheese")
cheddar = cheese.find_elements_by_id("cheddar")
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
IWebElement cheese = driver.FindElement(By.Id("cheese"));
IWebElement cheddar = cheese.FindElement(By.Id("cheddar"));
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
cheese = driver.find_element(id: "cheese")
cheddar = cheese.find_elements(id: "cheddar")
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
const cheese = await driver.findElement(By.id('cheese'));
const cheddar = await cheese.findElement(By.id('cheddar'));
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
val cheese = driver.findElement(By.id("cheese"))
val cheddar = cheese.findElement(By.id("cheddar"))
  {{< / code-panel >}}
{{< / code-tab >}}

之所以可以这样做，是因为 _WebDriver_ 和 _WebElement_ 类型都实现了 [_SearchContext_](//seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/SearchContext.html>SearchContext) 接口。
在WebDriver中，这称为基于角色的接口。基于角色的接口允许您确定特定的驱动程序实现是否支持给定的特性。这些接口定义得很清楚，并且尽量只承担单一的职责。
你可以在 [必须指定的其他部分](#) 中了解更多关于WebDriver的设计以及支持哪些驱动程序的角色。

<!-- TODO: A new section needs to be created for the above.-->

因此，上面使用的 _By_ 接口也支持许多附加的定位器策略。嵌套查找可能不是最有效的 cheese 位置策略，因为它需要向浏览器发出两个单独的命令;首先在DOM中搜索ID为“cheese”的元素，然后在狭窄的上下文中搜索“cheddar”。

为了稍微提高性能，我们应该尝试使用一个更具体的定位器：WebDriver 支持通过 CSS 定位器查找元素，允许我们将之前的两个定位器合并成一个搜索:

{{< code-tab >}}
  {{< code-panel language="java" >}}
driver.findElement(By.cssSelector("#cheese #cheddar"));
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
cheddar = driver.find_element_by_css_selector("#cheese #cheddar")
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
driver.FindElement(By.CssSelector("#cheese #cheddar"));
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
mucho_cheese = driver.find_elements(css: "#cheese #cheddar")
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
const cheddar = await driver.findElement(By.css('#cheese #cheddar'));
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
driver.findElement(By.cssSelector("#cheese #cheddar"))
  {{< / code-panel >}}
{{< / code-tab >}}

### 定位多个元素

我们正在处理的文件可能会有一个我们最喜欢的奶酪的订单列表:

```html
<ol id=cheese>
 <li id=cheddar>…
 <li id=brie>…
 <li id=rochefort>…
 <li id=camembert>…
</ul>
```

由于更多的奶酪无疑是更好的奶酪，而且必须单独取回每个商品很麻烦，因此一种更好的获取奶酪的技术是利用复数形式 `findElements(By)`。此方法返回 web 元素的集合。
如果只找到一个元素，它仍然返回(一个元素的)集合。如果没有匹配定位器的元素，将返回一个空列表。

{{< code-tab >}}
  {{< code-panel language="java" >}}
List<WebElement> muchoCheese = driver.findElements(By.cssSelector("#cheese li"));
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
mucho_cheese = driver.find_elements_by_css_selector("#cheese li")
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
IReadOnlyList<IWebElement> muchoCheese = driver.FindElements(By.CssSelector(“#cheese li”));
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
mucho_cheese = driver.find_elements(css: "#cheese li")
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
const muchoCheese = await driver.findElements(By.css('#cheese li'));
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
val muchoCheese: List<WebElement>  = driver.findElements(By.cssSelector("#cheese li"))
  {{< / code-panel >}}
{{< / code-tab >}}

### 元素选择策略

在 WebDriver 中有 8 种不同的内置元素定位策略:

| 定位器 | 说明 |
| -------- | ---------- |
| class name | 查找类名包含搜索值的元素(不允许使用复合类名) |
| css selector | 查找与 CSS 选择器匹配的元素 |
| id | 查找 ID 属性与搜索值匹配的元素 |
| name | 查找 name 属性与搜索值匹配的元素 |
| link text | 查找可见文本与搜索值匹配的链接元素 |
| partial link text | 查找其可见文本与搜索值部分匹配的链接元素 |
| tag name | 查找标记名称与搜索值匹配的元素 |
| xpath | 查找与 XPath 表达式匹配的元素 |

### Tips on using selectors

一般来说，如果 HTML id 是可用的、惟一的和一致可预测的，那么它们就是在页面上定位元素的首选方法。它们的工作速度非常快，可以避免复杂的 DOM 遍历带来的大量处理。

如果惟一的 id 不可用，那么一个编写良好的 CSS 选择器是定位元素的首选方法。XPath 可以像 CSS 选择器一样工作，但是语法很复杂，而且通常很难调试。虽然 XPath 选择器非常灵活，但它们通常没有经过浏览器厂商的性能测试，而且速度非常慢。

基于链接文本和部分链接文本的选择策略有其缺点，即只能对链接元素起作用。此外，它们在 WebDriver 内部调用 XPath 选择器。

标记名可能是一种危险的定位元素的方法。页面上经常出现同一标记的多个元素。这在调用返回元素集合的 _findElements(By)_ 方法时非常有用。

建议您尽可能保持定位器的紧凑性和可读性。要求 WebDriver 遍历 DOM 结构是一项昂贵的操作，而且搜索范围越窄越好。
