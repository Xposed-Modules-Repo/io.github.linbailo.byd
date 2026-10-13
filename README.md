# BYD 自动签到

比亚迪 App 的微信小程序每日自动签到。模块跑在微信进程内，直接反射取出小程序 login 的 code
并完成签到请求，**不需要 root，也不起本地端口**。

- 支持：Android 8.0+（minSdk 26）、LSPosed（Xposed API 82+）
- 作用域：仅 **微信**（`com.tencent.mm`）
- 包名：`io.github.linbailo.byd`

## 功能

- 小程序 login 时在微信进程内取出 code，再调用比亚迪的签到接口；
- 定时点 00:01 / 07:01 / 13:01 / 22:01，含启动补签与失败补签；
- 微信升级后自动 dex 探测适配（内置 10 个常见版本，其余靠本机探测生成）；
- 自带控制台 App：签到状态、日志、生效配置、版本适配、立即签到。

## 安装

1. 安装 Release 附件里的 APK；
2. LSPosed 管理器 → 模块 → 勾选「BYD 自动签到」，作用域勾选微信；
3. 强行停止微信后重新打开。

## 权限

`INTERNET`、`ACCESS_NETWORK_STATE`、`RECEIVE_BOOT_COMPLETED`、`SCHEDULE_EXACT_ALARM`。

## 说明

- 所有请求都在设备本地完成，不经过任何第三方服务器；
- 只签到自己账号的每日签到，没有批量或多账号操作；
- 源码与完整文档：https://github.com/linbailo/byd-lsp
