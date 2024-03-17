<p align="center">
  <a href="https://live.hsslive.cn" target="_blank">
    <img
      width="200"
      src="https://resource.hsslive.cn/billd-live/image/240160ddbc14367f7e0126c1f5b09b69.svg"
      alt="logo"
    />
  </a>
</p>

<h1 align="center">
  Billd-Live-Electron
</h1>

<p align="center">
 基于Electron + Vite4 + Vue3 + WebRTC搭建的直播间
</p>

## 简介

billd 直播间，目前实现了类似 [bilibili 的 Web 在线直播](https://live.bilibili.com)功能，即你（房主）可以发布直播，别人进入你的直播间后能看到你的直播内容；而你也可以作为观众，进入别人的直播间看别人的直播内容。

## 生态

| 名称         | 仓库                                                         | star & fork                                                  | 线上地址                                                     |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 直播间网页端 | [billd-live](https://github.com/galaxy-s10/billd-live)       | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live) | [https://live.hsslive.cn](https://live.hsslive.cn)           |
| 远程桌面     | [billd-desk](https://github.com/galaxy-s10/billd-desk)       | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-desk?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-desk) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-desk?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-desk) | [https://live.hsslive.cn/remoteDeskTop](https://live.hsslive.cn/remoteDeskTop) |
| 直播间移动端 | [billd-live-react-native](https://github.com/galaxy-s10/billd-live-react-native) | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live-react-native?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live-react-native) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live-react-native?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live-react-native) |                                                              |
| 直播间客户端 | [billd-live-electron](https://github.com/galaxy-s10/billd-live-electron) | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live-electron?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live-flutter) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live-electron?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live-electron) |                                                              |
| 直播间移动端 | [billd-live-flutter](https://github.com/galaxy-s10/billd-live-flutter) | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live-flutter?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live-flutter) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live-flutter?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live-flutter) |                                                              |
| 直播间移动端 | [billd-live-kotlin](https://github.com/galaxy-s10/billd-live-kotlin) | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live-kotlin?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live-kotlin) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live-kotlin?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live-kotlin) |                                                              |
| 直播间后台   | [billd-live-admin](https://github.com/galaxy-s10/billd-live-admin) | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live-admin?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live-admin) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live-admin?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live-admin) | [https://live-admin.hsslive.cn](https://live-admin.hsslive.cn) |
| 直播间后端   | [billd-live-server](https://github.com/galaxy-s10/billd-live-server) | [![github](https://img.shields.io/github/stars/galaxy-s10/billd-live-server?label=star&logo=GitHub)](https://github.com/galaxy-s10/billd-live-server) [![github](https://img.shields.io/github/forks/galaxy-s10/billd-live-server?label=fork&logo=GitHub)](https://github.com/galaxy-s10/billd-live-server) | [https://live-api.hsslive.cn](https://live-api.hsslive.cn)   |

## 功能

- [x] Web端发起远程控制
- [x] 客户端接收远程控制
- [ ] 客户端发起远程控制
- [ ] 文件传输

## 本地启动

- 安装依赖（建议使用 node 版本：v18.19.0）

```bash
pnpm i
```

> 更新 billd 相关依赖：

```bash
pnpm i billd-utils@latest billd-scss@latest billd-html-webpack-plugin@latest
```

- 运行

```bash
npm run dev
```

- 打包

```bash
npm run build
```

## 兼容性

- Windows
- macOS

## 常见问题

### rebuild

```sh
npm config set registry https://registry.npmmirror.com
```

```sh
./node_modules/.bin/electron-rebuild
```

### rebuild时cpu-feature报错

直接删了node_modules的cpu-feature

### pnpm安装electron时卡在postinstall

1. 直接ctrl+c退出npm安装
2. 进入node_modules/electron/install.js，将
   ```js
   downloadArtifact({
     version,
     artifactName: 'electron',
     force: process.env.force_no_cache === 'true',
     cacheRoot: process.env.electron_config_cache,
     checksums:
       process.env.electron_use_remote_checksums ??
       process.env.npm_config_electron_use_remote_checksums
         ? undefined
         : require('./checksums.json'),
     platform,
     arch,
   })
     .then(extractFile)
     .catch((err) => {
       console.error(err.stack);
       process.exit(1);
     });
   ```
   修改为：
   ```js
   downloadArtifact({
     version,
     artifactName: 'electron',
     force: process.env.force_no_cache === 'true',
     cacheRoot: process.env.electron_config_cache,
     checksums:
       process.env.electron_use_remote_checksums ??
       process.env.npm_config_electron_use_remote_checksums
         ? undefined
         : require('./checksums.json'),
     platform,
     arch,
     mirrorOptions: {
       mirror: 'https://npmmirror.com/mirrors/electron/',
       platform,
       arch,
     },
   })
     .then(extractFile)
     .catch((err) => {
       console.error(err.stack);
       process.exit(1);
     });
   ```
3. 在node_modules/electron目录下执行node install
