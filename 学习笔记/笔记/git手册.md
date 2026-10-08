## 1、将第三方开源代码迁移至个人 Gitee 仓库

> **目标仓库：** `git@gitee.com:luckydog886dx/ai-writing-platform.git`
> **适用场景：** GitHub 开源项目 → 搬运到 Gitee 二次开发 / 学习 / 国内加速

---
### 一、前置检查

```bash
git --version                          # 确认 Git 已安装
ssh -T git@gitee.com                   # 确认 SSH 连通 Gitee
pwd                                    # 确认在正确的目录
ls -d ai-writing-platform 2>/dev/null && echo "⚠️ 已存在" || echo "✅ 无冲突"
```

---
### 二、方案 A：Gitee 导入（推荐，3 分钟）

Gitee 右上角 `+` → **「从 GitHub/GitLab 导入仓库」** → 粘贴原仓库 GitHub 地址 → 填仓库名 `ai-writing-platform` → 点击导入。**同步更新时**直接在仓库页点「同步更新」按钮即可。

> **优点**：操作极简，Gitee 自动关联上游 | **缺点**：无法精细控制同步细节

---
### 三、方案 B：克隆 + 切换远程（最灵活，5 分钟）

```bash
# 1️⃣ 克隆原仓库
git clone https://github.com/xxx/ai-writing-platform.git
cd ai-writing-platform

# 2️⃣ 查看当前远程地址
git remote -v

# 3️⃣ 把 origin 从原仓库改成你的 Gitee
git remote set-url origin git@gitee.com:luckydog886dx/ai-writing-platform.git

# 4️⃣ 验证 & 推送
git remote -v
git push -u origin main             # -u 跟踪上游，之后只需 git push
git push origin --all && git push origin --tags   # 推送全部分支+标签
```

> **优点**：完全可控，可选择性修改历史 | **缺点**：原仓库更新需手动同步

---
### 四、进阶：双远程配置（origin→Gitee + upstream→原仓库）

```bash
# 克隆后配两个远程
git remote add upstream https://github.com/xxx/ai-writing-platform.git
git remote set-url origin git@gitee.com:luckydog886dx/ai-writing-platform.git
git remote -v   # 确认双远程生效

# 日后同步原仓库更新（四步走）
git fetch upstream           # 拉取原仓库最新代码
git checkout main
git merge upstream/main      # 合并到本地
git push origin main         # 推送到你的 Gitee
```

---
### 五、常见错误纠正

|     | 错误写法                   | 正确写法                          | 说明                                 |
| --- | ---------------------- | ----------------------------- | ---------------------------------- |
|     | `git add origin <URL>` | `git remote add origin <URL>` | `git add` 加文件，`git remote add` 加地址 |

**记忆口诀**：`git add` 加**文件**，`git remote add` 加**地址**。一个是暂存区，一个是通讯录。

---
### 六、远程地址管理速查

```bash
git remote -v                                # 查看所有远程
git remote add <名称> <URL>                   # 添加远程
git remote set-url <名称> <新URL>             # 修改远程 URL
git remote remove <名称>                      # 删除远程
git remote rename <旧名> <新名>              # 重命名
```

---
### 七、冲突处理

|     | 场景                | 命令                                                                         |
| --- | ----------------- | -------------------------------------------------------------------------- |
|     | 推送被拒绝（远程有本地没有的提交） | `git pull origin main --rebase` → `git push origin main`                   |
|     | 合并冲突              | `git status` → 编辑文件解决 `<<<<<` 标记 → `git add <文件>` → `git merge --continue` |
|     | 强制覆盖远程（慎用）        | `git push origin main --force-with-lease`（比 `--force` 安全）                  |

---
### 八、一键命令全集

```bash
# 克隆 → 配双远程 → 推送（可直接复制，替换 URL 后执行）
git clone https://github.com/xxx/ai-writing-platform.git
cd ai-writing-platform
git remote add upstream https://github.com/xxx/ai-writing-platform.git
git remote set-url origin git@gitee.com:luckydog886dx/ai-writing-platform.git
git remote -v
git push -u origin main
git push origin --all && git push origin --tags
echo "✅ 迁移完成"
```

```bash
# 日后同步上游更新
git fetch upstream && git checkout main && git merge upstream/main && git push origin main
echo "✅ 同步完成"
```

---
