# Academic Homepage for GitHub Pages

这是一个可直接放到 GitHub Pages 的个人学术主页模板，适合做：

- 个人主页
- 学术主页
- 论文展示页
- 项目与简历落地页

## 目录说明

- `_config.yml`：站点基础配置，主要改网站标题、邮箱、GitHub Pages 地址。
- `_data/profile.yml`：个人信息、简介、教育经历、项目、联系方式。
- `_data/publications.yml`：论文列表。
- `_layouts/default.html`：页面骨架。
- `assets/css/style.css`：样式文件。
- `index.md`：主页内容入口。

## 你只需要改这几个地方

1. 打开 `_config.yml`
2. 把 `title`、`email`、`url` 改成你的信息
3. 打开 `_data/profile.yml`
4. 把 `name`、`affiliation`、`bio`、`links`、`news`、`education`、`experience`、`projects` 改成你的内容
5. 打开 `_data/publications.yml`
6. 把示例论文替换成你的论文

## 怎么部署到 GitHub Pages

### 方式一：最标准

1. 在 GitHub 新建仓库：`你的用户名.github.io`
2. 把这个目录里的所有文件上传到仓库根目录
3. 等 GitHub 自动构建
4. 打开 `https://你的用户名.github.io`

### 方式二：项目仓库主页

1. 新建普通仓库，比如 `academic-homepage`
2. 上传这个目录里的所有文件
3. 在 GitHub 仓库设置里打开 `Pages`
4. 选择从默认分支部署
5. 最终地址通常是 `https://你的用户名.github.io/仓库名`

## 自定义建议

- 想放头像：把头像图片放进 `assets/images/`，然后在 `_data/profile.yml` 里把 `avatar` 改成 `/assets/images/你的图片名.jpg`
- 想放 CV：把 PDF 放进 `assets/docs/`，然后把链接改成对应路径
- 想加更多页面：可以新建 `projects.md`、`teaching.md`、`blog.md`
- 想改配色：主要看 `assets/css/style.css` 里的 `:root` 变量

## 本地预览

如果你本机装了 Ruby 和 Jekyll，可以在这个目录运行：

```powershell
bundle exec jekyll serve
```

然后打开本地地址预览。

如果你暂时不想装本地环境，也没关系，直接推到 GitHub Pages 一样可以用。
