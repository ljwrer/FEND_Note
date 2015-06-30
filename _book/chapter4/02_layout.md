## 布局解决方案

了解 CSS 中属性的值及其特性，
透彻分析问题和需求才可以选择和设计最适合的布局解决方案。

### 居中布局

#### 水平居中

![](../img/L/layout-center-horizontal.png)

子元素于父元素水平居中且其（子元素与父元素）宽度均可变。

##### inline-block + text-align

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .child {
    display: inline-block;
  }
  .parent {
    text-align: center;
  }
</style>
```

**优点**

- 兼容性佳（甚至可以兼容 IE 6 和 IE 7）

##### table + margin

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .child {
    display: table;
    margin: 0 auto;
  }
</style>
```

NOTE: `display: table` 在表现上类似 `block` 元素，但是宽度为内容宽。

**优点**

- 无需设置父元素样式 （支持 IE 8 及其以上版本）

NOTE：兼容 IE 8 一下版本需要调整为 `<table>` 的结果

##### absolute + transform

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    position: relative;
  }
  .child {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }
</style>
```

**优点**

- 绝对定位脱离文档流，不会对后续元素的布局造成影响。

**缺点**

- `transform` 为 CSS3 属性，有兼容性问题

##### flex + justify-content

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    display: flex;
    justify-content: center;
  }

  /* 或者下面的方法，可以达到一样的效果 */

  .parent {
    display: flex;
  }
  .child {
    margin: 0 auto;
  }
</style>
```

**优点**

- 只需设置父节点属性，无需设置子元素

**缺点**

- 有兼容性问题

#### 垂直居中

![](../img/L/layout-center-vertical.png)

子元素于父元素垂直居中且其（子元素与父元素）高度均可变。

##### table-cell + vertical-align

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    display: table-cell;
    vertical-align: middle;
  }
</style>
```

**优点**

- 兼容性好（支持 IE 8，一下版本需要调整页面结构至 `table`）

##### absolute + transform

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    position: relative;
  }
  .child {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }
</style>
```

**优点**

- 绝对定位脱离文档流，不会对后续元素的布局造成影响。

**缺点**

- `transform` 为 CSS3 属性，有兼容性问题

##### flex + align-items

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    display: flex;
    align-items: center;
  }
</style>
```

**优点**

- 只需设置父节点属性，无需设置子元素

**缺点**

- 有兼容性问题

#### 水平与垂直居中

![](../img/layout-center-center.png)

子元素于父元素**垂直及水平**居中且其（子元素与父元素）高度宽度均可变。

##### inline-block + text-align + table-cell + vertical-align

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    text-align: center;
    display: table-cell;
    vertical-align: middle;
  }
  .child {
    display: inline-block;
  }
</style>
```

**优点**

- 兼容性好

##### absolute + transform

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    position: relative;
  }
  .child {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }
</style>
```

**优点**

- 绝对定位脱离文档流，不会对后续元素的布局造成影响。

**缺点**

- `transform` 为 CSS3 属性，有兼容性问题

##### flex + justify-content + align-items

```html
<div class="parent">
  <div class="child">Demo</div>
</div>

<style>
  .parent {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
```

**优点**

- 只需设置父节点属性，无需设置子元素

**缺点**

- 有兼容性问题

### 多列布局



### 全屏布局