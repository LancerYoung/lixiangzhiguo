# lixiangzhiguo

Hot Seat（饭局聊天游戏）的**剧本发布仓库**。

- 这里只存**加密后的剧本产物**（`remote/*.enc`）+ 一份明文目录（`remote/remote_config.json`），
  明文剧本另有一个私有仓库维护。
- App 启动时只拉 `remote_config.json` 这份目录，比版本后按需下载单个剧本。

注意：仓库必须**公开**，否则 jsDelivr 拉不到，App 拿不到剧本。

## 目录说明

| 文件 | 说明 |
| --- | --- |
| `remote/remote_config.json` | 目录：版本号 + 每份剧本的元数据与 CDN 地址（明文） |
| `remote/<语言>__<uid>.enc` | 加密剧本（AES-256-CBC，密钥写在 App 二进制里） |

这里的加密只是「防随手抓取」级别的混淆，不是抗逆向——密钥在 App 里。
真要防，得上服务端 + 登录 + 动态密钥。

## 文件路径

剧本文件名用剧本 JSON 里的 `uid`，和源文件名解耦，源文件改名不影响发布和 App 取件。

```
remote/zh__<uid>.enc
```
