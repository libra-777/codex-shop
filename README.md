# 禾间小馆

基于 Vue 3 + Vite 的中文餐馆品牌展示首页。使用 JavaScript、Composition API 和单文件组件，支持菜品分类筛选与手机导航。

## 本地开发

需要 Node.js 20.19+ 或 22.12+，以及 npm。

```sh
npm install
npm run dev
```

打开终端显示的本地地址。

## 构建与预览

```sh
npm run build
npm run preview
```

生产文件生成于 `dist/`，可部署到静态托管服务。资源使用相对路径，支持部署到子目录。源码需经 Vite 处理，不支持直接双击 index.html 或用普通静态服务器运行源码。网站需要 JavaScript；禁用时显示启用提示。

## 内容维护

- `src/components/`：导航、首屏、菜品、故事、到店信息和页脚组件。
- `src/data/dishes.js`：六道示例菜品及分类、价格、图片与描述。
- `src/styles.css`：全局样式、响应式布局和减少动态效果设置。

品牌、价格、地址、电话均为示例。图片来自 Unsplash，属于氛围示意，需要网络加载。页面没有订座或点餐后台。
