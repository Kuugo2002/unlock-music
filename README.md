# 原项目仓库地址
https://git.unlock-music.dev/um/web

# Unlock Music 音乐解锁

- 在浏览器中解锁加密的音乐文件。 Unlock encrypted music file in the browser.
- Unlock Music 项目是以学习和技术研究的初衷创建的，修改、再分发时请遵循[授权协议]。
- Unlock Music 的 CLI 版本可以在 [unlock-music/cli] 找到，大批量转换建议使用 CLI 版本。
- CI 自动构建已经部署，可以在 [um-packages] 下载

[授权协议]: https://github.com/Kuugo2002/unlock-music/blob/main/LICENSE
[unlock-music/cli]: https://git.unlock-music.dev/um/cli
[um-packages]: https://git.unlock-music.dev/um/-/packages/generic/web-build/

## 特性

### 支持的格式

- [x] QQ 音乐 (.qmc0/.qmc2/.qmc3/.qmcflac/.qmcogg/.tkm)
- [x] Moo 音乐格式 (.bkcmp3/.bkcflac/...)
- [x] QQ 音乐 Tm 格式 (.tm0/.tm2/.tm3/.tm6)
- [x] QQ 音乐新格式 (.mflac/.mgg/.mflac0/.mgg1/.mggl)
- [x] <ruby>QQ 音乐海外版<rt>JOOX Music</rt></ruby> (.ofl_en)
- [x] 网易云音乐格式 (.ncm)
- [x] 虾米音乐格式 (.xm)
- [x] 酷我音乐格式 (.kwm)
- [x] 酷狗音乐格式 (.kgm/.vpr)
- [x] Android 版喜马拉雅文件格式 (.x2m/.x3m)
- [x] 咪咕音乐格式 (.mg3d)

### 其他特性

- [x] 在浏览器中解锁
- [x] 拖放文件
- [x] 批量解锁
- [x] 渐进式 Web 应用 (PWA)
- [x] 多线程
- [x] 写入和编辑元信息与专辑封面

## 使用方法

### 使用预构建版本

- 从 [Release] 或 [CI 构建][um-packages] 下载预构建的版本
  - :warning: 本地使用请下载`legacy版本`（`modern版本`只能通过 **http(s)协议** 访问）
- 解压缩后即可部署或本地使用（**请勿直接运行源代码**）

[release]: https://github.com/Kuugo2002/unlock-music/releases/latest

### 自行构建

- 环境要求
  - nodejs (v16.x)
  - npm

1. 获取项目源代码后安装相关依赖：

   ```sh
   npm install
   npm ci
   ```

2. 然后进行构建：

   ```sh
   npm run build
   ```

   - 构建后的产物可以在 `dist` 目录找到。
   - 如果是用于开发，可以执行 `npm run serve`。

3. 如需构建浏览器扩展，构建成功后还需要执行：

   ```sh
   npm run make-extension
   ```

### 在 cloudflare 上部署

1. 将本项目fork到自己的仓库
2. 在pages中进行构建
   ```sh
   # 构建命令
   NODE_OPTIONS=--openssl-legacy-provider npm run build
   # 部署命令
   npx wrangler deploy --assets=./dist --compatibility-date 2025-04-06 #根据你自己的日期进行修改
   ```

### 在 vercel 上部署
1. 将本项目fork到自己的仓库
2. 然后使用vue.js进行构建
   ```sh
   # 构建命令
   NODE_OPTIONS=--openssl-legacy-provider npm run build
   # 部署命令
   npm install && npm ci
   ```

## 注意事项
QQ音乐的版本不能超过19.51，可以在[Release]中下载。
