# axios

### 一、axios简介

```
axios用于基于promise对ajax的一种封装
```

### 二、基于Vue安装、使用、配置axios

#### 安装

* `npm`或`cnpm`安装axios包

  ```
  npm install --save axios vue-axios
  ```

* 将下面代码加入到`main.js`文件中

  ```js
  import axios from 'axios'
  import Vue from 'vue'
  
  Vue.prototy.axios = axios
  ```
  

#### 使用

```js
export default {
    data() {
        ···
    },
    
    methods: {
        this.axios.get('url地址')
    	// 响应回调函数
    	.then(res => {
    		// 显示回调数据
    		console.log(res.data)
		})
        // 错误回调函数
        .catch(err => {
            // 错误时显示
            console.log(err)
        })
    }
}
```

#### 配置

* 在main.js文件中进行配置

  ```js
  import Vue from 'vue'
  import axios from 'axios'
  Vue.prototype.axios = axios.create({
      // 相当于配置基础域名，不含路由
      baseURL: 'http://h25680249u.zicp.vip:18509',
      // 配置超时时间 10s ，超时则执行.catch函数
      timeout: 10000,
  })
  ```

### 三、

### 四、axios的请求方式

| 方法   | 作用     | 场景                   |
| ------ | -------- | ---------------------- |
| get    | 获取数据 | 一般用于加载数据       |
| post   | 提交数据 | 一般用于新建           |
| put    | 更新数据 | 一般用于修改           |
| patch  | 更新数据 | 用于数据量较大时的修改 |
| delete | 删除数据 | 一般用于删除           |

### 五、请求方式示例

#### get请求

* 写法1

    ```js
    // 不带参数传递
    this.axios.get('/api/test/')
    // 响应回调函数
    .then(res => {
        console.log(res)
    })
    .catch(err => {
        console.log(err)
    })

    // 带参数传递
    // 最终请求的路径为：http://localhost:8080/api/test/?id=1
    this.axios.get('/api/test/', {
        params: {
            id: 1,
        }
    })
    .then(res => {
        console.log(res)
    })
    .catch(err => {
        console.log(err)
    })
    ```
    
* 写法2（推荐）

    ```js
    // 不带参数传递
    this.axios({
    	method: 'get',
    	url: '/api/test/',
    }).then(res => {
    	console.log(res)
    }).catch(err => {
    	console.log(err)
    })
    
    // 带参数传递
    this.axios({
    	method: 'get',
    	url: '/api/test/',
    	params: {
    		id: 1,
    	}
    }).then(res => {
    	console.log(res)
    }).catch(err => {
    	console.log(err)
    })
    ```

#### post请求

```js
let params = {
	startDate: '2020-05-20',
	endDate: '2020-05-21',
}
this.axios({
	method: 'post',  // 请求方式不同
	url: '/api/test/',
	data: params,
}).then(res => {
	console.log(res)
}).catch(err => {
	console.log(err)
})
```

#### put请求

```js
let params = {
	id: 1,
	name: 'smile',
}
this.axios({
	method: 'put',  // 请求方式不同
	url: '/api/test/',
	data: params,
}).then(res => {
	console.log(res)
}).catch(err => {
	console.log(err)
})
```

#### patch请求

```js
let params = {
	id: 1,
	name: 'smile',
}
this.axios({
	method: 'patch',  // 请求方式不同
	url: '/api/test/',
	data: params,
}).then(res => {
	console.log(res)
}).catch(err => {
	console.log(err)
})
```

#### delete请求

```js
let params = {
	id: 1
}
this.axios({
	method: 'delete',
	url: '/api/test/',
	data: params,
}).then(res => {
	console.log(res)
}).catch(err => {
	console.log(err)
})
```

### 六、参考文献

+ axios中文文档：http://www.axios-js.com/zh-cn/docs/