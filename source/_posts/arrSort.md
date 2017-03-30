---
title: 排序去重
date: 2017-03-29 20:26:40
tags:
    - js
    - sort
commit: false
categories: js
---
### 数组去重和排序
#### 去重
```js
Array.prototype.unique=function() {
  var arr = [];
  this.sort();
  
  for(var i = 0, len = this.length; i < len; i++){
      if(this[i] != this[i+1]){
          arr.push(this[i])
      }
  }
  return arr;
}
var arr = [1, 1, 2, 4, 5, 3, 4, 5, 2];
console.log(arr.unique()) //[1, 2, 3, 4, 5]
```
<!--more-->
#### 排序
##### sort

```js
arr.sort((x1, x2) => {
    // return -1 // <0 [x1, x2]
    // return 1 // >0 [x2, x1]
    // return 0 // =0 [x1, x2]
})
```

##### 冒泡排序
- 每次从第一个开始冒泡
- 是否交换位置
    - 0-1 是否交换
    - 1-2 是否交换
    - 2-3 是否交换
    - 。。。
- arr[-1] //undefined < || > number false
- 最后一个不冒泡
- 数组被取值会先内部执行
    - var arr = [1, console.log(11)][0]
    - arr;  //11 1
    
```js
function bubbleSort(arr){
    var len = arr.length;
    for( var i = 0; i < len; i++){
        for(var j = 0; j < len-1; j++){
            if(arr[j] < arr[j-1]){
                arr[j] = [arr[j-1], arr[j-1]=arr[j]][0]
            }
            if(arr[j] == arr[j-1]){
                arr.splice(j, 1)
            }
        }
    }
}
```

##### 选择排序
- 选择个元素min 对比每个元素 找到比min小的元素
- 交互i和新的最小的min位置

```js
function selectSort(arr){
    var len = arr.length;
    var min;
    for(var i = 0; i < len; i++){
        min = i;
        for(var j =i; j < len; j++){
            if(arr[min] > arr[j]){
                min = j;
            }
        }
        if(min != i){
            arr[i] = [arr[min], arr[min] = arr[i]][0]
        }
    }
}

```
##### 快速排序
- 取一个中间数 num
- 与num比较大小 把数组切分成左右2组
- 递归继续排序
- 合并数组

```js
function quickSort(arr){
    var len = arr.length;
    if(len <= 1){
        return arr
    }
    var num = arr[Math.floor(len/2)];
    var left = [];
    var right = [];
    
    for(var i = 0; i < arr.length; i++){
        if(arr[i] == num) continue;
        arr[i] < num ? left.push(arr[i]) : right.push(arr[i])
    }
    return quickSort(left).concat(num, quickSort(right))
}

```