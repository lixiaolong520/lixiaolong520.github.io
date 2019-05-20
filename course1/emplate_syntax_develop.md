# 模板语法的发展


## Jsp + JSP 中EL表达式用法详解  
## Jquery拼接HTML代码片段

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

```
    var compiled = _.template("hello: <%= name %>");
    compiled({name: 'moe'});
    => "hello: moe"
```
```    
    var template = _.template("<b><%- value %></b>");
    template({value: '<script>'});
    => "<b>&lt;script&gt;</b>"
```

## Vue,React.Ng 语法
## 模板语法点= 循环,ifelse,嵌套，filter

## question:
+ 怎么做模板中的临时变量
  