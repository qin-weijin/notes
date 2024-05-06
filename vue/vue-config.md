```
export default defineConfig({
  baseUrl: '',
  publicPath: '/', // 部署入口  
  outputDir: 'dist', // 构建时输出路径。
  assetsDir: '', // 生成静态资源时输出路径。
  indexPath: 'index.html', // 生成 index.html 时输出路径
  filenameHashing: true, // 生成静态资源时是否包含 hash
  pages: { // 多页面配置选项。
    pageName: { entry, template, filename, title, chunks }
  }, 
  lintOnSave: true, // 开发环境中是否开启 eslint-loader
  runtimeCompiler: '', // 运行时编译器,可使用 template 选项
  transpileDependencies: '', // babel-loader 不忽略的 node_modules 文件
  productionSourceMap: '', // 生产环境的 source map 文件
  crossorigin: '',
  integrity: '',
  configureWebpack: Object | Function, // Webpack 配置选项。
  chainWebpack: Function, // Webpack 配置选项。
  css: { modules, requireModuleExtension, extract, soureMap, loaderOptions },
  devServer: 'open, host, port, https, hotOnly, overlay',// 开发服务器配置选项。
  proxy: '', // 设置代理
  parallel: '',// 启动 thread-loader
  pwa: '',// 插件配置选项。
  pluginOptions: { pluginName: {} } // 插件配置选项。
})
```