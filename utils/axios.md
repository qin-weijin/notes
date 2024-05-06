# Axios

Axios 基于 promise，服务端使用 node.js http 模块，客户端使用 XMLHttpRequests。

	$ npm i axios

## User

```ts
/** 
 * @path ./utils/request.ts
 * @description 定义请求方法 request(config, options)
 * @param config - Axios 请求参数
 * @param options - Request 函数配置项
*/
import axios from 'axios';

/* 创建 Axios 实例 */
const service = axios.create({ timeout: 6000 })

/* 拦截 request */
service.interceptors.request.use(
  (config) => { return config },
  (error) => { return Promise.reject(error) }
)

/* 拦截 response 在 .then 和 .catch 之前 */
service.interceptors.response.use(
  (response) => {
    if (response.data.code !== 200) {
      // 根据错误码处理
    } else { return response }
  },
  (error) => { return Promise.reject(error) }  
)

/* 定义请求方法 */
export const request = async <T = any>(
  config,
  options,
): Promise<T> => {
  try {
    const response = await service.request(config)
    return response
  } catch (error: any) {
    return Promise.reject(error)
  } 
}
```
```ts
/** 
 * @path ./utils/request.ts 
 * @description 定义 Axios 请求参数
*/
import { request } from '@/utils/request';
export function getImageCaptcha(params) {
  return request<API.CaptchaResult>({
    url: 'captcha/img',
    method: 'get',
    params,
  });
}
```

## 基本语法

```javascript
axios.get('/url', data).then(
  function (response) { console.log("请求成功时") }
).catch(
  function (error) { console.log("请求错误时") }
).finally(
  function () { console.log("总是执行") }
);
```

## 创建 Axios 实例

  const service = axios.create(AxiosRequestConfig)

**AxiosRequestConfig 请求配置**
```javascript
{
  url: '/user'
  method: 'get'
  baseURL: 'https://some-domain.com/api/'
  transformRequest: [function(data){ return data }]
  headers: {'X-Requested-With': XMLHttpRequest}
  params: { ID: 12345 }
  paramsSerializer: function(params){ return Qs.stringify(params, {arrayFormat: 'brackets'}) }
  data: 'Country=Brasil&City=Belo Horizonte'
  timeout: 1000
  withCredentials: false
  adapter: function (config) {}
  auth: { username: 'janedoe', password: 's00pers3cret' }
  responseType: 'json'
  responseEncoding: 'utf8'
  xsrfCookieName: 'XSRF-TOKEN'
  xsrfHeaderName: 'X-XSRF-TOKEN'
  onUploadProgress: function (progressEvent) {}
  onDownloadProgress: function (progressEvent) {}
  maxContentLength: 2000
  maxBodyLength: 2000
  validateStatus: function (status) { return status >= 200 && status < 300 }
  maxRedirects: 5
  socketPath: null
  httpAgent: new http.Agent({ keepAlive: true })
  httpsAgent: new https.Agent({ keepAlive: true })
  cancelToken: new CancelToken(function (cancel) {})
  decompress: true
  proxy: {
    protocol: 'https',
    host: '127.0.0.1',
    port: 9000,
    auth: { username: 'mikeymike', password: 'rapunz3l' }
  }
}
````
**实例方法**
```javascript
axios.request(config)
axios.get(url[, config])
axios.delete(url[, config])
axios.head(url[, config])   
axios.options(url[, config])   
axios.post(url[, data[, config]])   
axios.put(url[, data[, config]])   
axios.patch(url[, data[, config]])   
axios.getUri([config])   
```