# nautilus-git 扩展

## 安装
网站只提供到F26的copr仓库。只能自己动手（算不上编译）。
```
▶ git clone https://github.com/bil-elmoussaoui/nautilus-git
▶ di libappstream-glib-devel
▶ di ninja-build meson
▶ cd nautilus-git/
▶ meson builddir --prefix=/usr -Dfile_manager=nautilus
▶ sudo ninja -C builddir install
```
## bug
目前，目录顶部状态条显示，右侧菜单的“compare commits”完全无反映。
