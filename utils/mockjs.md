# Mockjs

生成随机数据，拦截 Ajax 请求。

- vite-plugin-mock

**Install**

	$ npm i mockjs -S
	$ npm i vite-plugin-mock -D

**文件目录**

```
./my-project
|- mock
|   └- mock_data              - 定义模拟数据
|- src 												- 必须在 src 内才能正确 $ npm run build
|   └- mock-prod-server.ts    - 初始化 Mock
└-vite.config.ts 							- 在 Vite 中配置 Mockjs
```

## 配置 `vite.config.ts`

```ts
import { viteMockServe } from 'vite-plugin-mock'
export default defineConfig({
  plugins: [
    viteMockServe({
        mockPath: 'mock',
        prodEnabled: true,
        injectCode: ` 
          import { setupProdMockServer } from './mock-prod-server';
          setupProdMockServer();
        `            
    })
  ],
})
```

**Config Options**

- `mockPath` - 指定入口
- `prodEnabled` - 在生产环境中打包运行 Mock 数据。 `$ npm run build`
- `injectCode` - 若 prodEnabled 开启则注入代码到 injectFlie 指定的文件路径。
- `injectFlie` - 设置代码注入路径。 `src/main.ts/js`
- `supportTs` - 读取 ts 模块
- `ignore` - 指定忽略文件格式
- `ignoreFiles` - 指定忽略文件
- `watchFiles` - 监听数据变化
- `localEnabled` - 开启本地 mock.ts 文件
- `configPath` - 设置读取的数据项
- `logger` - 显示请求日记

## 初始化 `mock-prod-server`
```javascript
import { createProdMockServer } from 'vite-plugin-mock/es/createProdMockServer'
/* 导入定义的模拟数据 */
const modules = import.meta.glob<Recordable>('./**/*.ts', { eager: true })
/* 定义创建 Mock 函数 */
export function setupProdMockServer() { createProdMockServer(mockModules) }
```

## 创建数据 `mock_data.ts`
```javascript
import type { MockMethod } from 'vite-plugin-mock';
export default [
  {
    url: '/mock-api/mock_data',
    method: 'get'
    timeout: 1000,
    statusCode: 200,     
    /* 非 JSON 响应 */
    rawResponse: async (req, res) => {},
    /* JSON 响应 */
    response: ({ query }) => { 
      return { 
      	code: 0, 
      	data: { name: 'vben' } 
      }                            
    },
  },
] as MockMethod[];
```