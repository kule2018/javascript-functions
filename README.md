# 一些常用的函数

## js实现LazyMan

[Lazyman.js](./lazyman/lazyman.js)

## js封装ajax,jsonp

[Ajax.js](./ajax/ajax.js)

## js双向绑定

[doublebinding.js](./doublebinding/doublebinding.js)

## js十种排序算法

[Sort.md](./sort/sort.md)

## 返回带逗号的数字

```
function numberWithCommas(x) {
  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g,',')  
}
```

## 数组去重

```javascript
Array.prototype.unique = function(){
  return [...new Set(this)]
}
```

```javascript
function unique(arr){
  let tempArr = []
  arr.map((v)=>{
    if(!(v in tempArr)){
      tempArr[tempArr.length] = v
    }
  })  
  return tempArr
}
```

```javascript
Array.prototype.unique = function(){
  let res = this.sort(),
  return res.filter((v,i,context)=>{
      return v !== context[i + 1]
  })
}
```

## 获取随机颜色值

```javascript
function getRandomColor(){
  let color = '#',
      letters = '0123456789abcdef'
  for(let i = 0;i<6;i++){
    color += letters[Math.round(Math.random() * letters.length)]
  }    
  return color
}
```

```javascript
function randomColor(){
  let color = 'rgba('
  for(i = 0; i < 3; i++){
    color += `${Math.round(Math.random() * 255)},`
  }
  return color += `${Math.random().toFixed(1)})`
}
```

## 数组乱序

```javascript
function shuffle(arr) {
    for (let i = arr.length; i; i--) {
        let j = Math.floor(Math.random() * i);
        [arr[i - 1], arr[j]] = [arr[j], arr[i - 1]]; //ES6解构赋值
    }
}
```

```javascript
[1,2,3,4,5].sort(() => {
    return Math.random() > .5 ? 1 : -1
})
```

```javascript
function shuffle(arr){
  let random = 0,result = [] ,origin = []
  arr.map(item => {origin.push(item)})
  while(arr.length > 0){
    random = Math.floor(Math.random() * arr.length) //生产原数组随机索引
    result.push(arr[random]) //向结果数组添加元素
    arr.splice(random, 1) //删除原数组元素
  }
  return {
    result,
    origin
  }   
}
```

## 数字求和

```javascript
function forSum(n){
  if(typeof n !== 'number'){
    return
  }
  let sum = 0
  for(n;n >= 1;n--){
    sum += n
  }
  return sum
}
```

## 冒泡排序

```javascript
function bubbleSort(arr){
  const len = arr.length
  for(let i = 0;i < len;i++){
    for(let j = 0;j < len - 1;j++){
      if(arr[j] > arr[j + 1]){
        [arr[j],arr[j+1]] = [arr[j+1],arr[j]]
      }
    }
  }
  return arr
}
```

## 字符串重复

```javascript
String.prototype.repeatify = String.prototype.repeatify ||
function(n){
  if(typeof n !== 'number') return
  let str =''
  for(let i=0;i<n;i++){
      str += this
  }
  return str
}
```

## 对象深拷贝

```javascript
function deepCopy(parent,child){
  child = child || {}
  if(typeof parent !== 'object'){
    return
  }  
  for(let item in parent){
    if(parent.hasOwnProperty(item)){
      if(typeof p[item] === 'object'){
        child[item] = Array.isArray(parent[item])? [] : {}
        deepCopy(parent[item],child[item])   
      }else{
        child[item] = parent[item]
      }
    }
  }
  return child
}
```

```javascript
const copy =  JSON.parse(JSON.stringify(source))
```

## 变量交换

```javascript
function change(a,b){
  return  [a,b] = [b,a]
}
```

## 寻找数组中最大值与最小值得差值

```javascript
function diff(arr){
  return Math.max(...arr) - Math.min(...arr)
}
```

## 获取n天前/后的日期

```javascript
function getDayBeforeAfter(date,type,days){
  date = date || new Date()
  type = type || 'after'
  days = days || 1

  if(!(date instanceof Date)){
    if(date.indexOf('-') != -1){
      date.replace(/\-/g,'/')
    }
    date = new Date(date)
  }
  let newDate = date
  switch (type){
    case "after":
        newDate = new Date(date.getTime() + (days * 24 * 60 * 60 * 1000))      
        break  
    case "before":
        newDate = new Date(date.getTime() - (days * 24 * 60 * 60 * 1000))
        break  
  }
  return `${newDate.getFullYear()}/` + `${newDate.getMonth() + 1}/` + `${newDate.getDate()}`
}
```

## 使用Promise对象处理ajax请求

```javascript
function promiseAjax(url){
  return new Promise(function(resolve,reject){
    const xhr = new XMLHttpRequest()
    xhr.open('GET',url,true)
    xhr.onload = function(){
      if(xhr.status >= 200 && xhr.status < 400 ){
        let data = JSON.parse(xhr.responseText)
        resovle(data)
      }else{
        reject(new Error(xhr.statusText))
      }
    }
    xhr.onerror = function(){
      reject(new Error(xhr.statusText))
    }
    xhr.send()
  })
}
let URL = 'http://news-at.zhihu.com/api/4/news/latest'
promiseAjax(URL).then(function(data){
  console.log(data)
}).catch(function(err){
  console.log(err)
})
```

## Fetch API

```javascript
const url = URL.fomat({
  pathname:''
})
const headers = new Headers({
  'Content-type':'application/json'  
})
const request = new Request(url,{
  method:'get',
  mode:'cors',
  credentials:'include',
  headers,
  body:JSON.stringify(body)
})
const reponse = await fetch(request)
const data = await reponse.json()
```

## 字符串重复

```javascript
String.prototype.repeatify = String.prototype.repeatify ||
function(n){
  if(typeof n !== 'number') return
  let str =''
  for(let i=0;i<n;i++){
      str += this
  }
  return str
}
```

## 数字左补全

```javascript
function leftPad(num){
  let n = parseInt(num,10)
  return n > 0 ? (n <= 9 ? '0'+n : n ) : '00'
}
```

## 斐波那契数列

```javascript
function fibonacci(n){
  const res = [1,1]
  if(typeof n !== 'number') return
  if(n === 0) return res
  while(n > 0){
    res.push(res[res.length -2] + res[res.length - 1])  
    n--
  }
  return res
}
```

## 阶乘
```javascript
function factorial (n) {
  function fact (n, res) {
    if (n < 2) return res
    return fact(n - 1, n * res)
  }
  return fact(n, 1)
}
```

## 生成随机字符串

```javascript
function getRandomString(n){
  if(typeof n != 'number') return
  let str = ""
  for(;str.length < n;str += Math.random().toString(36).substr(2)){}
  return str.substr(0,n)
}
```

## 将浮点数左边的数每3位加逗号
```javascript
function commafy (num) {
  return num && num.toString()
                   .replace(/(\d)(?=(\d{3})+\.)/g, ($1, $2) => {
                     return $2 += ','
                   })
}
```

## 函数防抖

```javascript
function debounce(fn,delay){
  let timer = null
  return function() {
    const self = this
    let args = arguments
    clearTimeout(timer)
    timer = setTimeout(()=>{
      fn.apply(self,args)  
    },delay)
  }
}
```
## 实现indexOf

```javascript
Array.prototype.indexOf = Array.prototype.indexOf ||
                          function (ele, fromIndex) {
                            if(this === null || !ele) {
                              return -1
                            }
                            let length = this.length
                            let i = fromIndex || 0
                            let cur = -1
                            while(true) {
                              if(this[i] === ele){
                                cur = i
                                break
                              }else {
                                i++
                                if(length === i){
                                  break
                                }
                                continue
                              }
                            }
                            return cur
                          }
```
