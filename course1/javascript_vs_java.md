# Java vs Javascript (es5)

1. get set方法
2. java是多线程,javascript是单线程
   对比手机开发android异步加载数据javasciprt可以直接在异步回调中操作dom
3. 面向对象编程
java class:
```java
public class Puppy{
   int puppyAge;
   public Puppy(String name){
      // 这个构造器仅有一个参数：name
      System.out.println("小狗的名字是 : " + name ); 
   }
 
   public void setAge( int age ){
       puppyAge = age;
   }
 
   public int getAge( ){
       System.out.println("小狗的年龄为 : " + puppyAge ); 
       return puppyAge;
   }
 
   public static void main(String[] args){
      /* 创建对象 */
      Puppy myPuppy = new Puppy( "tommy" );
      /* 通过方法来设定age */
      myPuppy.setAge( 2 );
      /* 调用另一个方法获取age */
      myPuppy.getAge( );
      /*你也可以像下面这样访问成员变量 */
      System.out.println("变量值 : " + myPuppy.puppyAge ); 
   }
}
```
javascipt:
```javascript
{
    stu:{
        name:'zhansan'
        age:23
    }
}
```
```javascript
    function Student(){
        this.name='zhansan'
        this.age='lisi'
    }
    Student.prototype.speak=function(){
        console.log(`My name is ${this.name}`)
    }
    Student.temp = '我是静态变量'
```
此处 name和age换到java里相当于字段,要区分清楚字段和属性的区别
此处要思考java里边get和set方法用途是什么，是不是必须要有的

4. lamda表达式 
5. java是强类型语言，javascript是弱类型语言（当然现在javascrpt可用通过Typescript或者Flow.js变相支持强类型)
6. java反射，javascript直接可以使用字符串创建Object
[java反射](https://www.cnblogs.com/bethunebtj/p/4680532.html)
7. 