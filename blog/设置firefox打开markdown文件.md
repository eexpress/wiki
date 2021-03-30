## 设置firefox打开markdown文件
```
⭕ cat ~/.local/share/mime/packages/text-markdown.xml
<?xml version="1.0"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
  <mime-type type="text/plain">
    <glob pattern="*.md"/>
    <glob pattern="*.mkd"/>
    <glob pattern="*.markdown"/>
  </mime-type>
</mime-info>

⭕ update-mime-database ~/.local/share/mime
```

---

## 安装firefox插件查看markdown文件
[GitLab Markdown Viewer](https://addons.mozilla.org/zh-CN/firefox/addon/gitlab-markdown-viewer/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)

---

## 安装firefox插件编辑markdown文件
[Markdown Editor for Firefox](https://addons.mozilla.org/zh-CN/firefox/addon/markdown-editor-premium/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)

---

## 安装独立的markdown本地web编辑器
- 下载 [editor.md](https://github.com/pandao/editor.md/archive/master.zip "editor.md") zip文件
- 解压到本地目录
- 参照 [说明](https://pandao.github.io/editor.md/ "说明") 建立index.html，注意修改html里面的路径，以指向解压的目录
- firefox 打开 index.html 便可编辑。

>  并没有看到打开/保存文件的功能。
>  和 **Markdown Editor for Firefox** 插件比较，这个附带有工具栏。

---

## 纯在线web编辑网站

[Dillinger](http://dillinger.io/)

[MaHua](http://mahua.jser.me/)