# front-end of NMSI

此文件夹中存放NMSI中的前端代码，使用vue.js构建

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```
# 代码结构

使用vue.js构建，app.vue作为主入口，在component中存放其他的页面。
为了顺应web2.0潮流以及更加舒适的交互体验，前端部分决定使用SPA的单页面方式构建。整体无刷新链接操作。
在页面中，主要分为登陆以及主页面。其中登陆页面负责验证个人信息以及用户。当密码和用户名正确以后将可以进入到主界面中。
暂时我们将只支持用户admin以及密码为123，后续用户注册将会在之后的迭代中开发。

# 使用到的技术

 - SPA单页面结构
 - vue.js框架构建
 - vue-router路由跳转
 - element-ui交互样式库
 - api.douban 豆瓣电影接口
 
# 第一次迭代
 - 增加基本的登陆页面和电影主页面的架构
 - 完成各项将会使用到的函数以及接口的设计
 - 引入elemnt-ui以及vue-router等技术，为将来的各种功能做基本的插件库引入

# 第二次迭代
 - 引入豆瓣电影接口，可以获取到时下热门的电影资讯，方便我们直接得到电影数据发送给后台
 - 持续开发前端交互，增加多种交互
 - 增加选座系统
 
# 代码规范

## html语法
用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。嵌套元素应当缩进一次（即两个空格）。对于属性的定义，确保全部使用双引号，绝不要使用单引号。不要在自闭合（self-closing）元素的尾部添加斜线 -- HTML5 规范中明确说明这是可选的。不要省略可选的结束标签（closing tag）（例如， 或 ）
### HTML DOCTYPE
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。
ie兼容模式字符编码通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。
### 引入文件
根据HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 type 属性，因为 text/css 和 text/javascript 分别是它们的默认值。
### 实用
尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。
### 属性顺序
HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。
classid,namedata-*src,for,type,href,valuetitlerole,aria- *class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。
### JavaScript 生成的标签
通过JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。

## CSS
### 语法
用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。为选择器分组时，将单独的选择器单独放在一行。为了代码的易读性，在每个声明块的左花括号前添加一个空格。声明块的右花括号应当单独成行。每条声明语句的 : 后应该插入一个空格。为了获得更准确的错误报告，每条声明都应该独占一行。所有声明语句都应当以分号结尾。最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错。对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，box-shadow）。不要在 rgb()、rgba()、hsl()、hsla() 或 rect() 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。十六进制值应该全部小写，例如，#fff。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。尽量使用简写形式的十六进制值，例如，用 #fff 代替 #ffffff。为选择器中的属性添加双引号，例如，input[type="text"]。只有在某些情况下是可选的，但是，为了代码的一致性，建议都加上双引号。避免为 0 值指定单位，例如，用 margin: 0; 代替 margin: 0px;。

### 声明顺序
相关的属性声明应当归为一组，并按照下面的顺序排列：
Positioning Box model Typographic Visual

### 媒体查询（Media query）的位置
将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

### 单行规则声明
对于只包含一条声明的样式，为了易读性和便于快速编辑，建议将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。
这样做的关键因素是为了错误检测 -- 例如，CSS 校验器指出在 183 行有语法错误。如果是单行单条声明，你就不会忽略这个错误；如果是单行多条声明的话，你就要仔细分析避免漏掉错误了

### 简写属性的声明
在需要显示地设置所有值的情况下，应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：
paddingmarginfontbackgroundborderborder-radius

### 注释
代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。
对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。
### class命名
class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思。class 名称应当尽可能短，并且意义明确。使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称。基于最近的父 class 或基本（base） class 作为新 class 的前缀。使用.js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。
## js编码规范
### 命名规范
驼峰命名法
大驼峰
小驼峰
文件资源命名法
文件名不得使用空格文件名使用小写，不使用大写包含多个单词时候，单个单词之间建议使用-分割引入资源使用相对路径，不要指定资源所带的具体协议 ( http:,https: ) ，除非这两者协议都不可用。
### 变量命名
命名规则：小驼峰式
### 函数命名
命名规则：普通函数使用小驼峰式，构造函数使用大驼峰式
### 常量
命名规则：全部大写
### 类的成员
公共属性和方法：同变量命名方式 -私有属性和方法：前缀为下划线_后面跟公共属性和方法一样的命名方式

### 注释规范
单行注释
单独一行：//与注释文字之间保留一个空格在代码后面注释： //与代码有一个空格注释代码：//与代码之间保留一个空格
多行注释

/**
@param grid {Ext,Grid,Panel} 需要合并的Grid,合并Grid的行 -@param cols {Array} 需要合并列的Index值，从0开始计数@param isAllSome {Boolean} 是否两个tr完全一样才能合并true：完全一样，false：默认@return volid@author@example
*/
