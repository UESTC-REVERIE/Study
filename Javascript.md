## Javascript

----

### 基础语法

#### 箭头函数和匿名函数：

1. 箭头函数：

   ```js
   (param,...) => {
       
   }
   ```

2. 匿名函数：

   ```js
   (function(param){
       
   })(InputParam);
   ```

   

### DOM

#### setTimeout

```js
function myFunc(param1,param2){
    
} 
//function 1
setTimeout(myFunc,timeout,param1,param2);
//function 2
setTimeout( () => {

},timeout)
//function 3
setTimeout( function(){
    
},timeout)
```

