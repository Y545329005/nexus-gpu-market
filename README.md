# Nexus 算力平台 · GPU·Market 原型

P2P 算力市场交互原型（租户 + 宿主 + 平台管理端），单文件、零构建：React 18 UMD + Babel standalone + Tailwind，全部经 CDN 加载，浏览器直接打开即可运行。

## 在线预览

- 主原型（租户 / 宿主双视角）：<https://y545329005.github.io/nexus-gpu-market/proto/index.html>
- 平台管理端（出金审批 / 抽成 / 风控）：<https://y545329005.github.io/nexus-gpu-market/proto/admin.html>

> 首屏加载需访问 CDN，请确保网络可访问 `cdn.jsdelivr.net`。

## 本地运行

方式一（零依赖）：直接用浏览器打开 `proto/index.html`。

方式二（Vite 本地服务）：

```bash
npm install
npm run dev
# 打开 http://localhost:8787/proto/index.html
```

## 页面与角色

| 入口 | 说明 |
|---|---|
| `proto/index.html` | 租户 + 宿主单文件原型。右上角「→ 宿主视角」切换双主体 |
| `proto/admin.html` | 平台管理端：大盘 / 市场管理 / 资金对账（抽成滑杆 + 出金审批）/ 用户与合规 |

核心演示链路：

- **租户**：搜索报价 → 选机器 → 双 SKU（按量 / 时段订单·预订）→ 计费状态机 → 账单流水
- **宿主**：上架向导（Agent 化）→ 收益实时入账 → 收益页「提现」弹窗（通道 / 金额 / 实到预估）→ 申请制出金
- **平台**：Admin 实时看见申请 → 批准/驳回 → 用户端秒级到账（幂等不重复扣）
- **双端联动**：`index.html` 与 `admin.html` 同源共享 localStorage，双开演示「用户操作 → 后台实时亮灯 → 后台干预 → 用户端生效」

## 演示账号

- 注册：任意邮箱（如 `test@demo.dev`）+ 密码 `password123` + 任意 6 位验证码
- Admin 端内置演示账号，见 `proto/admin.html`

## 文档

- `proto/README.md` —— 原型功能全景与走查脚本
- `proto/DEMO.md` —— 14 分钟演示脚本（分幕）

## 说明

- 本仓库为产品原型 / 可点击规格说明，非生产代码；数据均为演示 mock。
- 价格、费率、对账口径等标注为演示口径的部分，以正式 PRD 为准。
