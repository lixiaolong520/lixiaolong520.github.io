# 模板语法的发展


## Jsp + JSP 中EL表达式用法详解  
[El 表达式](https://www.jb51.net/article/105314.htm)

## Jquery拼接HTML代码片段
```javascript
   var html = '<div>';
   html += 'helloworld';
   html+= '<div>';
   dom.innerHTML = html;

```
## Jsrender
[jsrender API](https://www.jsviews.com/)
Here's a first example of the power and simplicity of JsRender templates: Some data:
```json
[
  {
    "name": "Robert",
    "nickname": "Bob",
    "showNickname": true
  },
  {
    "name": "Susan",
    "nickname": "Sue",
    "showNickname": false
  }
]
```
A template (with a conditional section using an {{if...}} tag):
```html
<div>
   <em>Name:</em> {{:name}}
   {{if showNickname && nickname}}
      (Goes by <em>{{:nickname}}</em>)
   {{/if}}
</div>
```



## underscore小型模板语法
[_.template API](https://underscorejs.org/#template)

```javascript
    var compiled = _.template("hello: <%= name %>");
    compiled({name: 'moe'});
    //=> "hello: moe"
```
## Vue,React.Ng 语法
## 模板语法点= 循环,ifelse,嵌套，filter

## question:
+ 怎么做模板中的临时变量
+ 只用Jquery，不适用Mvvm怎么简化表单的编写
  