---
title: "对AUT执行操作*"
weight: 4
---

您可以使用 sendKeys 方法设置元素的文本，如下所示：

{{< code-tab >}}
  {{< code-panel language="java" >}}
String name = "Charles";
driver.findElement(By.name("name")).sendKeys(name);
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
name = "Charles"
driver.find_element_by_name("name").send_keys(name)
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
string name = "Charles";
driver.FindElement(By.Name("name")).SendKeys(name);
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
name = "Charles"
driver.find_element(name: "name").send_keys(name)
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
const name = "Charles";
await driver.findElement(By.name('name')).sendKeys(name);
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
val name = "Charles"
driver.findElement(By.name("name")).sendKeys(name)
  {{< / code-panel >}}
{{< / code-tab >}}

一些Web应用程序使用 JavaScript 库来添加拖放功能。以下是将一个元素拖到另一个元素上的基本示例：

{{< code-tab >}}
  {{< code-panel language="java" >}}
WebElement source = driver.findElement(By.id("source"));
WebElement target = driver.findElement(By.id("target"));
new Actions(driver).dragAndDrop(source, target).build().perform();
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
source = driver.find_element_by_id("source")
target = driver.find_element_by_id("target")
ActionChains(driver).drag_and_drop(source, target).perform()
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
IWebElement source = driver.FindElement(By.Id("source"));
IWebElement target = driver.FindElement(By.Id("target"));
new Actions(driver).DragAndDrop(source, target).Build().Perform();
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
source = driver.find_element(id: "source")
target = driver.find_element(id: "target")
driver.action.drag_and_drop(source, target).perform
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
const actions = driver.actions({bridge: true});
const source = await driver.findElement(By.id('source'));
const target = await driver.findElement(By.id('target'));
await actions.dragAndDrop(source, target).perform();
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
val source = driver.findElement(By.id("source"))
val target = driver.findElement(By.id("target"))
Actions(driver).dragAndDrop(source, target).build().perform()
  {{< / code-panel >}}
{{< / code-tab >}}

### 点击一个元素

您可以使用click方法单击一个元素：

{{< code-tab >}}
  {{< code-panel language="java" >}}
driver.findElement(By.cssSelector("input[type='submit']")).click();
  {{< / code-panel >}}
  {{< code-panel language="python" >}}
driver.find_element_by_css_selector("input[type='submit']").click()
  {{< / code-panel >}}
  {{< code-panel language="csharp" >}}
driver.FindElement(By.CssSelector("input[type='submit']")).Click();
  {{< / code-panel >}}
  {{< code-panel language="ruby" >}}
driver.find_element(css: "input[type='submit']").click
  {{< / code-panel >}}
  {{< code-panel language="javascript" >}}
await driver.findElement(By.css("input[type='submit']")).click();
  {{< / code-panel >}}
  {{< code-panel language="kotlin" >}}
driver.findElement(By.cssSelector("input[type='submit']")).click()
  {{< / code-panel >}}
{{< / code-tab >}}

***AUT**: 被测应用程序
