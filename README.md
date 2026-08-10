# Pont for LazyCat

[Pont](https://github.com/dockers-x/pont) 是一个支持 Cloudflare Quick Tunnel 和 ngrok 的 Web 隧道管理服务。本仓库将其打包为 LazyCat LPK v2。

- 软件包：`community.lazycat.app.pont`
- 上游镜像：`ghcr.io/dockers-x/pont`
- 目标平台：Linux amd64

## 本地验证

本项目不需要本地 Docker，也没有 buildscript：

```bash
mkdir -p dist
lzc-cli project release -o dist/application.lpk
lzc-cli lpk info dist/application.lpk
```

## 自动更新与发布

`.github/workflows/publish.yml` 每天检查上游稳定 SemVer 标签，也支持手动触发。发现新版本后，GitHub Action 会复制目标架构镜像到 LazyCat Registry、构建并验证 LPK、创建版本化 GitHub Release Asset，并分别发布到 LazyCat 官方商店与喵喵商店。

必需的 GitHub Actions Secrets：

- `LZC_API_TOKEN`
- `APPSTORE_URL`
- `APPSTORE_TOKEN`

可选 Secrets：

- `LZC_API_HOST`
- `APP_ID`
- `PRIVATE_STORE_GROUP_CODES`

Organization Secrets 必须显式授权本仓库。相同名称同时存在时，Environment Secret 优先于 Repository Secret，Repository Secret 优先于 Organization Secret。
