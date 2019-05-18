## 数组去重的几种方法
- 双循环一(需排序)

 ```
 arr.sort((a,b)=>a - b)
for(var i = 0; i < arr.length; i++){
    for(var j  = 1; j < arr.length-1 ; j++){
        if(arr[i] === arr[j]){
           arr.splice(arr[j], 1)
        }
    }
}
console.log(arr)
 ```
 
 - 双循环二(取数组中的每个值跟剩余值比较，此方法比较耗费性能)
 
 ```
 for(var i = 0; i < arr.length; i++){
    let item = arr[i]
    for(var k = i+1; k < arr.length; k++){
        if(item === arr[k]){
            arr.splice(k,1)
        }
    }
}
console.log(arr)
 ```
- ES6 set

```
let arr1 = new Set(arr)
console.log(arr1)
```
- indexOf
```
let arr1 = []
for(i in arr){
    if(arr1.indexOf(arr[i]) === -1 ){
        arr1.push(arr[i])
    }
}
console.log(arr1)
```
- 原地删除重复项 

```
for (i = 0; i < arr.length; i++) {
    if (arr[i] == arr[i+1]) {
        arr.splice(i, 1);
        i--; //避免数组塌陷
    }
}
console.log(arr)
```
- 基于对象键值对方式处理

```
var obj = {}
for(i = 0; i < arr.length; i++){
    var item  = arr[i]
    if(typeof obj[item] !== 'undefined'){
        arr.splice(i,1)
        i--
    }else{
        obj[item] = item
    }
}
console.log(arr)
```
