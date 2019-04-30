没半点音讯怎续风陵夜话，见不到大哥哥愿知他如何行侠； 
* `Route::get('/', array('as' => 'adminIndex', 'uses' => 'IndexController@getWelcome'));`  
似乎可以通过@来指定一个类中的方法
----
### 框架逻辑   
```flow
st=>start: 开始
e=>end: 结束
op=>operation: 我的操作
cond=>condition: 确认？

st->op->cond
cond(yes)->e
cond(no)->op
```
