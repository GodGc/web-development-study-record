# 2018-03-12

1. 先记录一个有点难度的JS面试题
   1.  ```js
      function test(){
              var n = 4399;
              function add(){
                  n++;
                  console.log(n);
              }

              return {n:n,add:add};
      //          返回了一个有着值为n的属性n和值为add的方法add的匿名对象，
      //          在这里，在这个匿名对象中，属性n和方法add是互不相关的，
      //          即使在闭包add中改变了变量n的值，result.n的值依然不变。可以console.log(test())查看一下
      //          会返回一个匿名对象
      }

          var result = test();
          var result2 = test();
          result.add();   //4399++=4400 此时{n:n}中n的值被缓存 n=4400
          //第一次执行后，闭包函数的n值始终保持在内存中，所以第二次执行时会在第一次基础上+1
          result.add();   //再次调用时，先从n=4400开始进入add(),然后n++变为4401
          console.log(result.n); //查看第23行
          result2.add();  //    函数封装好之后，result和result2各自有自己的的test作用域，
                          //    所以最后的result2.add()的结果是4400
      ```

      所以最后的输出结果：4400、4401、4399、4400

   2. 涉及到了闭包、变量作用域的问题，附录一个阮一峰大神关于JavaScript闭包的帖子 

              [click here](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)：http://www.ruanyifeng.com/blog/2009/08/learning\_javascript\_closures.html
2. 移动端web的click时间具有延迟性，比正常反应延迟0.2s



