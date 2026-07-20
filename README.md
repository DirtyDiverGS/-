[README.md](https://github.com/user-attachments/files/30194538/README.md)
# 回击台 Reply Desk

> AI 网络争议回复助手。针对网络喷子、恶意评论、抬杠、疑似造谣和性别争议观点，生成有力度但文明、合法、可核验的中文回复。

![Version](https://img.shields.io/badge/version-V0.0.1-b2412e)
![Platform](https://img.shields.io/badge/platform-Windows-202322)
![Runtime](https://img.shields.io/badge/runtime-PowerShell-267057)

## 功能

- 强硬回击、文明方言口吻、阴阳怪气、抬杠拆解、捧杀反讽和证据追问。
- 支持自定义回复风格，可指定口吻、句式、节奏和收尾方式。
- 可生成单版回复或三种结构明显不同的回复。
- 支持 DeepSeek、OpenAI、硅基流动和自定义 OpenAI 兼容接口。
- 没有 API Key 时自动使用本地规则生成。
- API Key 仅在当前页面内存和单次本机转发请求中使用，不写入磁盘。

## 快速开始

### 便携版

1. 下载并解压 `ReplyDesk-V0.0.1-Windows-Portable.zip`。
2. 双击 `启动工具.bat`。
3. 浏览器会自动打开回击台。
4. 粘贴需要回应的内容，选择场景和风格，然后生成回复。

工具会自动选择可用的本机端口。如果浏览器没有自动打开，请复制 PowerShell 窗口中 `Reply Desk started:` 后面的地址。

### 源码运行

项目无需安装第三方依赖。直接在项目目录运行：

```bat
启动工具.bat
```

## AI 配置

展开页面中的“AI 接口设置”，选择供应商和模型，然后填写对应的 API Key。

| 供应商 | 接口预设 | 可选模型 |
| --- | --- | --- |
| DeepSeek | `https://api.deepseek.com/v1` | `deepseek-chat`、`deepseek-reasoner` |
| OpenAI | `https://api.openai.com/v1` | GPT-4.1 系列等 |
| 硅基流动 | `https://api.siliconflow.cn/v1` | DeepSeek V3、DeepSeek R1 |
| 自定义 | 用户填写 | OpenAI Chat Completions 兼容模型 |

AI 功能必须通过 `启动工具.bat` 打开。直接双击 `index.html` 会受到浏览器跨域策略限制。

## 回复风格

- **强硬回击**：直接指出结论、证据和推理问题。
- **方言口吻**：使用地区口语节奏和语气词，不生成方言脏话。
- **阴阳怪气**：使用短句、反问、反差和回马枪。
- **抬杠拆解**：识别偷换概念、以偏概全、双重标准等问题。
- **捧杀反讽**：先表面认可，再指出证据或前提缺失。
- **证据追问**：追问来源、样本、口径、时间和适用边界。
- **自定义风格**：由用户填写具体表达要求。

## 安全边界

回击台只针对观点、论证和公开行为，不针对个人或群体身份。

- 不生成脏话、人格侮辱、威胁或歧视内容。
- 不提供人肉搜索、开盒或其他违法建议。
- 不捏造事实、数据、案例、法律条文和来源。
- 性别议题只回应具体观点，不攻击男性、女性或其他性别群体。
- 生成结果仍需用户核对事实、来源和上下文。

## 隐私

- 本地服务只监听 `127.0.0.1`，不会向局域网开放。
- 页面不使用 Cookie、`localStorage`、数据库或日志文件。
- API Key 不会保存到项目目录或浏览器存储。
- 仅向用户选择的 AI 接口发送生成所需内容。

## 项目结构

```text
.
|-- index.html          # 前端界面和回复逻辑
|-- server.ps1          # 本地静态服务和 AI 请求代理
|-- 启动工具.bat        # Windows 启动入口
|-- 使用说明.txt        # 简明使用说明
|-- VERSION             # 当前版本
`-- dist/               # 便携版压缩包和校验文件
```

## 当前版本

`V0.0.1`

便携包发布时同时提供 `.sha256` 文件，可使用以下命令校验：

```powershell
Get-FileHash .\ReplyDesk-V0.0.1-Windows-Portable.zip -Algorithm SHA256
```
