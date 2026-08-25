# UniTranslate Fullstack

这是一个本地整理的 UniTranslate monorepo，包含：

- `backend/`: UniTranslate 后端与内置控制台服务
- `web-console/`: UniTranslate 独立 Web 控制台

## 本地启动

```bash
docker compose up -d --build
```

服务地址：

- 后端 / 内置控制台: http://localhost:9431/
- API 管理密钥: `123456`

## 独立前端开发

```bash
cd web-console
npm install
npm run dev -- --host 0.0.0.0
```

独立前端地址默认是 http://localhost:5173/，开发环境 API 指向 `http://localhost:9431`。

## 本地修复说明

当前版本包含以下本地修复：

- FreeGoogle 翻译遇到空行时不再导致整次请求失败。
- Web 控制台提交翻译前会过滤空行。
- 冷缓存未命中时会明确进入真实翻译流程。
- 容器配置存储改为 MySQL，避免重建容器后翻译平台配置丢失。
