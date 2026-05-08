# Zernio 调研看板（独立预览）

跟 echo-app 主项目代码完全独立，**不影响**任何主项目逻辑。

## 目录结构

```
preview/zernio-tracker/
├── index.html      ← 可视化页面
├── data.json       ← 数据源（要更新就改这个）
├── deploy.sh       ← 一键部署到线上
└── README.md       ← 本说明
```

## 怎么本地预览

```bash
cd preview/zernio-tracker
python3 -m http.server 8765
# 浏览器打开 http://localhost:8765
```

> 不能直接双击 `index.html` —— 浏览器安全策略不允许 `file://` 读 JSON。

## 怎么更新数据

改 `data.json` → 浏览器刷新页面 → 立刻看到新效果。

## 怎么部署到线上

### 首次部署前的一次性准备

旧的 `competitor-tracker` 仓库已经不再使用。Zernio 看板对应一个**新的 GitHub 仓库**，需要先手动创建：

1. 浏览器打开 https://github.com/new
2. Repository name 填 `zernio-tracker`
3. 选 **Public**，勾选 "Add a README file"（必须勾，否则 clone 失败）
4. 点 Create repository
5. 进入仓库 → **Settings → Pages** → Source 选 `Deploy from a branch`，Branch 选 `main / (root)` → Save

### 之后每次更新

```bash
bash preview/zernio-tracker/deploy.sh
# 或自定义 commit：
bash preview/zernio-tracker/deploy.sh "更新 add-on 价格"
```

线上地址：<https://lia270.github.io/zernio-tracker/>

## 数据源

- https://zernio.com/
- https://zernio.com/pricing
- https://zernio.com/features
- https://zernio.com/blog/white-label-social-media-scheduler

## 跟 docs/ 里的 Markdown 是什么关系

- `docs/zernio-integration-assessment.md` —— 完整书面调研报告
- `preview/zernio-tracker/` —— 可视化看板，给老板/合伙人远程看

两份内容同步；本看板的数据来自调研报告的整理。
