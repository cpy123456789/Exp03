# Axios123
------
### 1.Axios引言
原生AJAX使用复杂，且本身是针对MVC的编程，不符合现在前端MVVM的浪潮，
且JQUERY整个包太大，如果单纯只使用其中的AJAX却要导入整个JQUERY非常的不合理


前端MVC案例(DOM)：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script src="vue.js"></script>
<body>
  
        <div></div>
        <input type="text">
    <script>
       var input = document.querySelector('input');
       var div = document.querySelector('div');
      document.onkeyup = function(e) {   //通过DOM操作
            var html = input.value;
            div.innerHTML = html;
       }
    </script>
</body>
</html>
```
前端MVVM案例(双向数据绑定)
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script src="vue.js"></script>
<body>
    <div id="app">
        <div>{{msg}}</div>
        <input type="text" v-model='msg'>
    </div>
    <script>
        var vm = new Vue({
            el:'#app',
            data:{
                msg:''   //通过双向数据绑定
            }
        })
    </script>
</body>
</html>

```
<br/>
### 2.Axio安装 <br>
```

2.1 使用npm的方式引入
```
$ npm install axios
```
2.2 使用CDN的方式引入
```
<script src=“https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js”></script>
或者
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>

```
2.3 下载到本地引入
```
下载地址：https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js
```
2.42.使用bower的方式引入
```
$ bower install axios
```

<br/>
###3.Axios的使用方式
3.1 GET不带参数

```
axios.Get()不带参数：
axios.get('http://localhost:8080/axios/cpy')
                   .then(ret => {
                       console.log(ret.data)
                   })

```

3.2 axios.Get()携带参数：


```
axios.get('http://localhost:8080/axios/getName',{
                    params:{
                        name:“呵呵”
                    }
              })
                   .then(ret => {
                        console.log(ret.data)
                    })

```

3.3 axios.Post()不带参数：

```
axios.post('http://localhost:8080/axios/cpy')
                   .then(ret => {
                       console.log(ret.data)
                   })

```

3.4 axios.Post()携带参数
catch()函数为请求发生错误时进行响应的**回调函数**，catch()函数能够接收异常信息
```
axios.post('http://localhost:8080/axios/getName',{
                                           name:“呵呵”
                    }
               })
                   .then(ret => {
                        console.log(ret.data)
                    })

```

3.5 axios.Put()不带参数：

```
axios.put('http://localhost:8080/axios/cpy')
                   .then(ret => {
                       console.log(ret.data)
                   })

```

> 3.6 axios.Put()携带参数：



```
 axios.put('http://localhost:8080/axios/getName',{
                    
                        name:“呵呵”
                    }
               )
                   .then(ret => {
                        console.log(ret.data)
                    })

```

> 3.7 axios.Delete()不带参数：
```
axios.delete('http://localhost:8080/axios/cpy')
                   .then(ret => {
                       console.log(ret.data)
                   })

```

> 3.8 axios.Delete()携带参数：
```
 axios.delete('http://localhost:8080/axios/getName',{
                    params:{
                        name:“呵呵”
                    }
                })
                   .then(ret => {
                        console.log(ret.data)
                    })


```
3.9 并发请求
场景：一个页面的数据来源于多个互不关联的请求，需要统一处理后然后呈现. <br><br>
用到的API：1.axios.all(iterable)    参数：请求数组 <br>
2.axios.spread(callback)  参数：对应请求返回值


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<body>
 
    <script>
      axios.all([
      axios.get("http://localhost:8080/axios/noparams1", {  
        
      }),
      axios.post('http://localhost:8080/axios/noparams2') 
    ]).then(axios.spread((resdata, rescity) => {
      // 上面两个请求都完成后，才按顺序执行这个回调方法
      console.log('resdata', resdata)
      console.log('rescity', rescity)
    }))
    </script>
</body>
</html>

```

4.1 请求配置
发出请求可用的配置选项，只有url是必须的，如果未指定方法，请求将默认为GET

```
url :用于请求服务器的url
Method:发出请求时的请求方法，默认为get
baseURL:基础域名的设置
Headers:要发送的自定义请求头
Params:要发送的URL参数
Timeout:如果请求的时间超过timeout,请求被终止
responseTyple:默认为JSON字符串
maxRedirects:5定义在NODE.JS中要遵循的重定向最大数量

```



