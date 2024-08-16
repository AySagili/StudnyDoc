# Vue3 常用插件

### 自动导包

代码

#自动导入

#安装 unplugin-vue-components 和 unplugin-auto-import 插件

npm install -D unplugin-vue-components unplugin-auto-import

```js
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";

//unplugin
import AutoImport from "unplugin-auto-import/vite";
import Components from "unplugin-vue-components/vite";
import { ElementPlusResolver } from "unplugin-vue-components/resolvers";
import Icons from "unplugin-icons/vite"; //图标
import IconsResolver from "unplugin-icons/resolver";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue(),

    AutoImport({
      // 自动导入 Vue 相关函数，如：ref, reactive, toRef 等
      imports: ["vue"],

      resolvers: [
        ElementPlusResolver(),
        // 自动导入图标组件
        IconsResolver(),
      ],
    }),
    Components({
      resolvers: [
        ElementPlusResolver(),
        // 自动注册图标组件
        IconsResolver({
          enabledCollections: ["ep"],
        }),
      ],
    }),

    Icons({
      autoInstall: true,
    }),
  ],
});
```

```js
import { createApp } from "vue";

/*
    //整体导入 ElementPlus 组件库
    import ElementPlus from 'element-plus' //导入 ElementPlus 组件库的所有模块和功能 
    import 'element-plus/dist/index.css' //导入 ElementPlus 组件库所需的全局 CSS 样式
    import * as ElementPlusIconsVue from '@element-plus/icons-vue' //导入 ElementPlus 组件库中的所有图标
    import zhCn from 'element-plus/dist/locale/zh-cn.mjs' //导入 ElementPlus 组件库的中文语言包
    */

import App from "./App.vue";

const app = createApp(App);

/*
    //注册 ElementPlus 组件库中的所有图标到全局 Vue 应用中
    for (const [key, component] of Object.entries(ElementPlusIconsVue)) {
        app.component(key, component)
    }
    //app.use(ElementPlus) //将 ElementPlus 插件注册到 Vue 应用中s
    app.use(ElementPlus, {
        locale: zhCn // 设置 ElementPlus 组件库的区域语言为中文简体
    })
    */

app.mount("#app");
```
