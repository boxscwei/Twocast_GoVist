# Twocast - AI播客生成器

官网: [Twocast.app](https://twocast.app/)

![Sceenshot](./public/assets/img/image.png)

## 特性
- 可生成3~5分钟播客
- 根据主题生成
- 根据链接生成
- 根据 doc, pdf, txt 等文档生成
- 根据列表页，生成 5~9 分钟播客
- 支持多语言
- 可下载
- 播客内容包括音频、大纲、脚本
- 支持3大平台 Fish Audio, Minimax, Google Gemini

## 示例

- English: [Hacker News Hot Articles](https://twocast.app/podcast/vs962a7f-9461-4875-b7c7-2f5aca66126e)
- 中文: [Hacker News 热榜](https://twocast.app/podcast/vs789e71-b192-4374-93a2-8177f457ba5c)
- 中文: [V2EX热榜](https://twocast.app/podcast/vsbed589-6493-4ac2-8217-64d82b1ecafa)

## 方法一：本地启动

### 启动依赖服务
```
docker run -t -d --restart always -p 8080:8080 -e PORT=8080 --name textract bespaloff/textract-rest-api:v4.0.2
docker run -d --restart always --name ffmpeg-api -p 8081:3000 kazhar/ffmpeg-api
```

### 配置环境
```
cp .env.example .env
```

详细内容参考 [.env配置](#env配置)

### 启动 postgres
- 创建数据库 twocast
- 修改 .env 配置 `DATABASE_URL=`
- 运行 `npx drizzle-kit push` 初始化数据库

### 启动
```
yarn && yarn start
```

## 方法二：从 Docker 启动（可能出错）

### 配置环境
```
cp .env.docker .env
```

详细内容参考 [.env配置](#env配置)

### 启动
```
docker compose up
```


## .env配置

### 在 .env 配置 TTS API

- [Fish Audio](https://bit.ly/4k7AXHt)
  - 进入 [Fish Audio](https://bit.ly/4k7AXHt) 拿到 api-key 并填入 `FISH_AUDIO_TOKEN=`
- Minimax (非必须)
  - 进入 [Profile](https://www.minimax.io/platform/user-center/basic-information) 拿到 GroupID 并填入 `MINIMAX_GROUP_ID=`
  - 进入 [API keys](https://www.minimax.io/platform/user-center/basic-information/interface-key) 拿到 api-key 并填入 `MINIMAX_TOKEN=`
  - 设置 `MINIMAX_ENABLED=1`
- Google Gemini (非必须，很贵)
  - 进入 [Google AI Studio](https://aistudio.google.com/gen-media) 拿到 api-key 并填入 `GEMINI_TOKEN=`
  - 设置 `GEMINI_ENABLED=1`

### 在 .env 配置 LLM API
- Chat: 进入 https://openrouter.ai 拿到 api-key 并填入 `LLM_API_KEY=`
- Search: 进入 https://console.x.ai/ 拿到 api-key 并填入 `LLM_SEARCH_API_KEY=`

## 鸣谢
- https://github.com/PxlSyl/tailwind-nextjs-starter-blog-i18n