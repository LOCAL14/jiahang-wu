# 部署说明：Jia-Hang Wu 学术主页（al-folio）

目标仓库：`https://github.com/LOCAL14/jiahang-wu`  
预期站点：`https://local14.github.io/jiahang-wu/`

本目录内容已按吴佳航（Jia-Hang Wu）定制。**本机（box）未配置 GitHub 凭据，请勿在此环境 `git push`。** 请用已登录 GitHub 的机器或 Cursor Cloud Agent 推送。

## 1. 在 GitHub 建空仓库

1. 打开 <https://github.com/new>（账号 `LOCAL14`）。
2. Repository name：`jiahang-wu`
3. 选 **Public**
4. **不要**勾选 Add README / .gitignore / license（保持空仓，避免首次推送冲突）
5. Create repository

> 也可用 al-folio 的 “Use this template”，但当前目录已是定制好的完整站点，直接推空仓更简单。

## 2. 推送本目录到仓库

在**已登录 GitHub** 的机器上：

```bash
cd /path/to/jiahang-wu-al-folio

# 若仍指向 alshedivat/al-folio，改成你的仓库
git remote remove origin 2>/dev/null || true
git remote add origin https://github.com/LOCAL14/jiahang-wu.git

# 建议新建干净提交（可选：保留 al-folio 历史也可）
git checkout -B main
git add -A
git status   # 确认无密钥、无 .env
git commit -m "Personalize al-folio site for Jia-Hang Wu (吴佳航)"
git push -u origin main
```

SSH 示例：`git remote add origin git@github.com:LOCAL14/jiahang-wu.git`

## 3. 开启 GitHub Pages（Actions）

1. 仓库 → **Settings** → **Pages**
2. Build and deployment → Source：**GitHub Actions**
3. 推送后工作流 `.github/workflows/deploy.yml` 会自动跑（也可在 Actions 里手动 **Deploy site** → Run workflow）
4. 等待绿色勾；约 1–3 分钟后访问：  
   **https://local14.github.io/jiahang-wu/**

### 关键注意

- `_config.yml` 已设：
  - `url: https://local14.github.io`
  - `baseurl: /jiahang-wu`
- 若以后改成用户根站 `https://local14.github.io/`（仓库名须为 `LOCAL14.github.io`），把 `baseurl` 改成空 `""` 并改 `url`。
- 仓库名或用户名变更时，务必同步改 `url` / `baseurl`。

## 4. 推送后建议立刻做的事

| 项 | 说明 |
|----|------|
| 头像 | 替换 `assets/img/prof_pic.jpg` 为本人照片（勿热链 Scholar） |
| ORCID | 注册后在 `_data/socials.yml` 取消注释并填 `orcid_id` |
| Semantic Scholar / LinkedIn | 同上填 `semanticscholar_id` / `linkedin_username` |
| 完整作者表 | 部分 BibTeX 用了 `and others`；有出版社 PDF 后补全 |
| 演示博客 | `_posts/` 仍有 al-folio 演示文，导航已隐藏；不需要可整目录删掉再推 |
| CV | `_pages/cv.md` 导航已关；有 PDF 再开 `nav: true` 并改 `_data/socials.yml` |

## 5. 本地预览（可选）

官方推荐 Docker（见 `docs/INSTALL.md`）：

```bash
docker compose up
# 浏览器打开提示的本地地址
```

或 `bundle install && bundle exec jekyll serve`（需 Ruby 3.3+）。

## 6. 联系与数据来源

- 邮箱：`230249190@seu.edu.cn`
- Google Scholar：https://scholar.google.com/citations?user=Zhlz684AAAAJ
- 论文列表来源：旧站 `/workspace/jiahang-wu-academic-site/publications/`（含 DOI）；已写入 `_bibliography/papers.bib`（17 篇；一作 `selected: true`）
