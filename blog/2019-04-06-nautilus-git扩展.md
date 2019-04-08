# nautilus-git 扩展

## 安装
网站只提供到F26的copr仓库。只能自己动手（算不上编译）。
```
▶ git clone https://github.com/bil-elmoussaoui/nautilus-git
▶ di libappstream-glib-devel    <---重要
▶ di ninja-build meson
▶ cd nautilus-git/
▶ meson builddir --prefix=/usr -Dfile_manager=nautilus
▶ sudo ninja -C builddir install
```
## bug
目前，目录顶部状态条显示不变色/不出修改计数的图标，右侧菜单的“compare commits”显示带ansi颜色序列，看来没认真做事。也没有commit+push。作者说重写，不太相信这懒人。
