## Axios

> Create by **gintangible** on **2019-6-5 23:46**  

[中文文档](https://www.kancloud.cn/yunye/axios/234845)


Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。

功能：
* 从浏览器中创建 XMLHttpRequests
* 从 node.js 创建 http 请求
* 支持 Promise API
* 拦截请求和响应
* 转换请求数据和响应数据
* 取消请求
* 自动转换 JSON 数据
* 客户端支持防御 XSRF

### 1. 安装

用 npm:

`npm install axios`

使用 bower:

`bower install axios`

使用 cdn:

`<script src="https://unpkg.com/axios/dist/axios.min.js"></script>`

### 2. 使用方法

axios 的常用使用方式。

1. get

```
// 为给定 ID 的 user 创建请求
axios
    .get('/user?ID=12345')
    .then(function(response) {
        console.log(response);
    })
    .catch(function(error) {
        console.log(error);
    });

// params
axios
    .get('/user', {
        params: {
            ID: 12345
        }
    })
    .then(function(response) {
        console.log(response);
    })
    .catch(function(error) {
        console.log(error);
    });
```

2. post

```
axios
    .post('/user', {
        ID: 12345
    })
    .then(function(response) {
        console.log(response);
    })
    .catch(function(error) {
        console.log(error);
    });

```

3. 执行多个并发请求

```
function getUserAccount() {
    return axios.get('/user/account');
}

function getUserPermissions() {
    return axios.get('/user/permissions');
}

axios.all([getUserAccount(), getUserPermissions()]).then(
    axios.spread(function(acct, perms) {
        // 两个请求都执行完成
        console.log(acct);
        console.log(perms);
    })
);
```

4. 配置请求

```
axios({
    method: 'get',
    url: '/user',
    params: {
        ID: '123123'
    }
});
```

### 3. 配合`Vue`使用

1. 于 `utils` 文件夹内创建 `fetch.js` 即 `axios` 封装的拦截函数。

> fetch.js

```
import axios from 'axios';

// 创建axios实例
const service = axios.create({
    baseURL: process.env.BASE_API, // api的base_url
    timeout: 5000 // 请求超时时间
});

// request拦截器
service.interceptors.request.use(
    config => {
        // 在发送请求之前做些什么，比如添加 token 等
        return config;
    },
    error => {
        // 请求错误
        console.log('request: ' + error); // for debug
        Promise.reject(error);
    }
);

// respone拦截器
service.interceptors.response.use(
    response => {
        // 对响应的数据做些处理
        return response;
    },
    error => {
      // 对响应错误做些处理
        console.log('response: ' + error); // for debug
        return Promise.reject(error);
    }
);

export default service;
```

2. 创建 `api` 文件夹，对请求的接口进行分类

> api/user.js

```
import fetch from '@/utils/fetch';

export function getUser(token) {
    return fetch({
        url: 'url/info',
        method: 'get',
        parmas: {
            token
        }
    });
}
```

3. views 内使用

> pageA.vue

```
<script>
    import { getUser } from '@/api/user';

    methods: {
        getInfo() {
            getUser.then(response => {
                console.log(response);
            }, error => {
                console.log(error);
            })
        }
    }
<script>
```





