# 自定义域名绑定指南

将 `live.clutchreframe.com` 绑定到 GitHub Pages 的完整操作步骤。

---

## 步骤 1：CNAME 文件（已完成）

仓库根目录的 `CNAME` 文件内容为 `live.clutchreframe.com`，已推送。

---

## 步骤 2：Cloudflare DNS 详细操作

### 2.1 登录 Cloudflare

1. 浏览器打开 **https://dash.cloudflare.com**
2. 用你的账号密码登录

### 2.2 选择域名

1. 登录后会看到 **Home** 页面，列出你所有的域名
2. 找到并点击 **clutchreframe.com**（点域名卡片本身，不是旁边的按钮）
3. 进入该域名的管理面板

### 2.3 进入 DNS 设置

1. 在左侧导航栏中，找到 **DNS** 菜单项（带一个地球/网络图标）
2. 点击 **DNS** → 会展开子菜单，点击 **Records**（记录）
3. 现在你应该看到 **DNS management** 页面，上面列出已有的 DNS 记录

### 2.4 添加 CNAME 记录

1. 点击页面上方的蓝色按钮 **Add record**（添加记录）
2. 出现一行新的表单，按以下填写：

| 字段 | 填写内容 |
|------|----------|
| **Type**（类型） | 下拉选择 `CNAME` |
| **Name**（名称） | 输入 `live` |
| **Target**（目标） | 输入 `clutchreframe.github.io` |
| **Proxy status**（代理状态） | 点击橙色云朵图标，切换为 **灰色云朵**（DNS only） |
| **TTL** | 保持默认 `Auto` 即可 |

3. 点击 **Save**（保存）

### 2.5 关于代理状态（非常重要）

- 默认新建记录时云朵是 **橙色**（Proxied），你必须 **点击它切换为灰色**
- 灰色 = **DNS only**，表示流量直接到 GitHub Pages
- 橙色 = **Proxied**，流量经过 Cloudflare 代理，会导致 GitHub Pages 无法签发 HTTPS 证书
- 切换方法：点击那个云朵图标，它会在橙色和灰色之间切换

---

## 步骤 3：GitHub Pages Custom Domain

1. 打开 https://github.com/ClutchReframe/live-website/settings/pages
2. 找到 **Custom domain** 输入框，输入 `live.clutchreframe.com`
3. 点击 **Save**
4. 等待页面显示 DNS 检查通过（绿色勾）
5. 勾选 **Enforce HTTPS**（如果 DNS 还没生效，这个选项可能暂时不可用，等几分钟再试）

---

## 验证

配置完成后（DNS 生效可能需要几分钟到数小时），依次验证：

1. `https://live.clutchreframe.com` — 应显示首页
2. `https://live.clutchreframe.com/privacy.html` — 隐私政策
3. `https://live.clutchreframe.com/terms.html` — 服务条款
4. `https://live.clutchreframe.com/riot.txt` — 应返回纯文本 UUID
