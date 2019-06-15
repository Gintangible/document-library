# Axios

> Create by **gintangible** on **2019-6-5 23:46**  
> Recently revised in **2019-6-5 17:00**

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

## 1. 安装

用 npm:

`npm install axios`

使用 bower:

`bower install axios`

使用 cdn:

`<script src="https://unpkg.com/axios/dist/axios.min.js"></script>`

## 2. 使用方法

1. get

```
// 为给定 ID 的 user 创建请求
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

```

2.post

## 3. 配合`Vue`使用



