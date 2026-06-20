# One2 优化版（文件夹结构）

这是对原站点的静态前端重构版本。项目不依赖前端框架或构建工具，可直接部署到 GitHub Pages、Nginx、Apache、对象存储或任意静态托管平台。

## 目录结构

```text
one2-optimized/
├─ index.html                 # 页面结构
├─ assets/
│  ├─ css/
│  │  ├─ base.css             # 变量、重置、通用排版
│  │  ├─ components.css       # 页面组件
│  │  └─ responsive.css       # 响应式规则
│  ├─ js/
│  │  ├─ config.js            # 站点、接口、联系方式、价格配置
│  │  ├─ data.js              # 本地模型与节点数据
│  │  ├─ api.js               # API 请求封装
│  │  ├─ ui.js                # 弹窗、Toast 等 UI 能力
│  │  └─ app.js               # 页面初始化与业务交互
│  └─ images/
│     ├─ logo.svg
│     └─ favicon.svg
├─ docs/
│  ├─ 接口说明.md
│  └─ 优化说明.md
├─ 404.html
└─ README.md
```

## 本地运行

可直接双击 `index.html` 查看。推荐使用本地静态服务器：

```bash
python -m http.server 8080
```

然后访问 `http://localhost:8080/`。

## 部署到 GitHub Pages

1. 将本目录内容上传到仓库根目录。
2. 打开仓库 Settings → Pages。
3. Source 选择 `Deploy from a branch`。
4. 选择目标分支和 `/ (root)`。
5. 保存并等待部署完成。

## 接入现有后端

编辑 `assets/js/config.js`：

```js
apiBase: 'https://你的接口域名',
mockMode: false,
```

接口字段参考 `docs/接口说明.md`。若前后端域名不同，请在服务端正确配置 CORS，并在生产环境启用 HTTPS。

## 修改内容

- 站点名称、联系方式、价格：`assets/js/config.js`
- 模型和节点卡片：`assets/js/data.js`
- 色彩和尺寸变量：`assets/css/base.css` 顶部 `:root`
- 页面模块与文字：`index.html`

## 上线前检查

- 将演示价格、客服信息、公告替换为真实内容。
- 将 `mockMode` 设置为 `false` 并验证所有接口。
- 不要在前端文件中放置 API 密钥、数据库密码或后台管理凭证。
- 登录接口必须使用 HTTPS，并由服务端设置安全 Cookie。
