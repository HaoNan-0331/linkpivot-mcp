# LinkPivot MCP 扩展包生态

[灵枢 LinkPivot](https://github.com/HaoNan-0331) 的 MCP（Model Context Protocol）扩展包集合。每个 `.mcpb` 包对接一类设备的 REST API，导入灵枢后即可让 AI 助手直接调用设备的能力——查状态、改配置、抓日志，全程受灵枢的命令安全闸（黑名单硬底 / 白名单 / 越权拦截强确认）管控。

## 下载使用

1. 在下方 [Releases](../../releases) 页下载对应设备的 `.mcpb` 包
2. 打开灵枢 → MCP 管理 → 导入包
3. 按配置向导绑定设备：填写设备管理地址与凭证（凭证加密存储在本地，仅在你机器上）

> 灵枢本体（Windows 安装包）的下载入口即将开放。

## 包总表

| 包 | 对接设备 | 工具数 | 版本 | 状态 |
|----|---------|-------|------|------|
| nsfocus-nf-mcp | 绿盟 NF 系列防火墙（北向 REST API） | 183 | 0.2.0 | ✅ 可下载 |
| yaxin-firewall-mcp | 亚信安全防火墙 | 23 | 0.1.0 | ✅ 可下载 |
| playwright-browser-mcp | 浏览器自动化（通用工具，非设备对接） | 24 | 0.0.79 | ✅ 可下载 |
| asg-firewall-mcp | 上元信安 ASG 防火墙 | 166 | 0.1.0 | 即将上线 |
| hillstone-mcp | 山石网科防火墙 | 94 | 0.1.0 | 即将上线 |

持续上新中。每对接一款新设备会发布新的 `.mcpb` 包。

## 开发自己的 .mcpb 包

`.mcpb` 是一个 zip 分发格式：`manifest.json` 描述清单 + 服务程序（node 或内嵌 Python 运行时，离线可用）。完整字段约束、双轨打包规则、体积与安全校验要求见 **[mcpb-format-spec.md](mcpb-format-spec.md)**。

按规范打好包后可在灵枢中导入验证；欢迎通过 Issue 提交你想对接的设备型号。

## 安全说明

- 所有包只封装设备自身提供的 REST API，不含任何后门或额外通道
- 凭证（token / 密码）不打包在 `.mcpb` 内，导入后由灵枢按设备绑定填写并加密存储
- 本仓库所有工具仅用于**已获授权**的设备运维；高危操作在灵枢侧另有确认闸与审计日志

## 许可

本仓库的包与文档采用 [MIT License](LICENSE)。包内嵌的 Python 运行时及第三方依赖（mcp、httpx、pydantic、playwright 等）遵循其各自的开源协议。
