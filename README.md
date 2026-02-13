# pig-plugin-tsperson

> TeamSpeak 在线人数查询插件 - [pig-sender](https://github.com/PJWaurora/pig-sender) QQ 机器人模块

## 功能

- **在线人数查询** — `@机器人 查询人数` 查询当前 TS 服务器在线用户并生成状态卡片
- **服务器状态** — 展示服务器名称、在线人数、频道数、运行时长等信息
- **进出通知** — 定时轮询 TS3 ServerQuery API，检测用户进出变化并自动推送通知
- **通知控制** — 群内可通过命令开关进出通知
- **深色主题卡片** — 使用 PIL 原生渲染暗色主题卡片，展示在线用户列表和进出变动

## 架构

```
tsperson/
├── manifest.json        # 模块元信息与配置 schema
├── tsperson.py          # 主模块（TSPersonModule）— 消息处理 & 图片渲染
└── ts3_client.py        # TS3 ServerQuery 客户端封装
```

## 配置

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `host` | string | `""` | TeamSpeak 服务器地址（必填） |
| `poll_interval` | number | `60` | 轮询间隔（秒） |
| `enable_notify` | boolean | `true` | 是否启用进出通知 |
| `notify_groups` | array | `[]` | 接收通知的群号列表 |
| `serverQuery.port` | string | `"10011"` | ServerQuery 端口 |
| `serverQuery.client_id` | string | `""` | ServerQuery 用户名 |
| `serverQuery.client_password` | string | `""` | ServerQuery 密码 |

## 使用方法

```
@机器人 查询人数    # 查询在线人数
@机器人 查询人类    # 同上
@机器人 ts状态     # 查看详细状态
@机器人 ts通知开   # 开启本群进出通知
@机器人 ts通知关   # 关闭本群进出通知
```

## 依赖

- `ts3` — TeamSpeak 3 ServerQuery Python 库
- `Pillow` — 图片渲染

## 许可

MIT
