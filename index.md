[gimmick:forkmeongithub(color: 'red', position: 'right')](https://github.com/eexpress/wiki)

## 2019年

###04
- [安装rime输入法](blog/2019-04-15-中州韵.md)
- [手动解决fedora包冲突](blog/2019-04-09-包冲突导致游戏不运行.md)
- [测试hugo](blog/2019-04-08-测试hugo.md)
- [手贱一次lvm](blog/2019-04-07-lvm.md)
- [残缺的nautilus-git](blog/2019-04-06-nautilus-git扩展.md)
- [方便的vim通用编译函数](blog/2019-04-02-vim动态执行编译.md)
- [cairo画图过程分析](blog/2019-04-01-cairo画图过程分析.md)
- [本地化vala手册](blog/2019-04-02-本地化vala手册.md)
- [hexo安装和完全卸载](blog/2019-04-01-hexo笔记.md)

### 03
> 2个vala项目

[cairo-timer](https://github.com/eexpress/cairo-timer)|[showit](https://github.com/eexpress/showit)
:--:|:--:
![](pic/timer.png)![](pic/timer-old.png)|![](pic/showit.png)
03-28 启动|03-23 启动

### 02
- [新系统安装(fedora,lenovo)](blog/2019-02-13-新系统安装.md)

## 之前
[hexo版本的blog。2005-2019.4](https://eexpress.github.io/hexo-blog)

> 源里面有`hugo`，类似hexo。终于可以去掉乱七八糟的node.js了。

## 关于本站点

采用`mdwiki`搭建。

- 相关文档：
	- [mdwiki 帮助文档](https://dynalon.github.io/mdwiki/#!tutorials/github.md)
	- [mdwiki 仓库地址](https://github.com/Dynalon/mdwiki/) !! This project is currently unmaintained!!
- 缺点：
	1. 非动态，所以无法搜索内容。有人外挂强行动态管理，但有点不KISS。
	1. 非动态，只能手动更新索引页面。外挂脚本可能搞定。其实想到一个好处，不想放出来的页面，不写链接即可。
	1. 没找到自定义css的方法。
	1. 没有RSS了。不过hexo的rss最近出现混乱，不搞了也好。
- 优点：
	1. 干净。不和html和js打交道。不像`dokuwiki`或者`tiddlywiki`(单文件结构，好像现在也和node.js勾搭上了)。
	1. 服务器无要求，纯客户端实时渲染。
- 实际操作
    1. 舒服。虽然索引链接要手动添加。过程相当于写一个文章，再改下index.md，其实都只是markdown的编辑而已。retext工作很好。
    1. 提交就完成，少好多事情啊。不要安装npm的破东西，只差一步ci+push，几乎都不要打开终端了（坐等那懒散的nautilus-git扩展的作者重写他的破py，如果干脆不改进了，一跺脚我就上vala）。
- 