g2编译（build）后文件在vue项目中直接 import G2 from './g2.js'会报错"export 'default' (imported as 'G2') was not found in './g2.js'，识别G2为undefined,导致Cannot read property 'Chart' of undefined,这是重现repo（临时解决方案：把编译后文件内容覆盖到./node_modules/@antv/g2/build/g2.js并import G2 from '@antv/g2'）。大概率是因为webpack配置导致的编译问题，因为小程序项目对编译后文件，直接var MyF2 = require('./my-f2').default 可用。

使用私有npm仓库安装也可解决该问题，解决该问题后可对比polyfill后g2和原生g2区别。
# g2_canvas

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
