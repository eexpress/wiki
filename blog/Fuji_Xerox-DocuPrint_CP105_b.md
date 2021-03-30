## 编译

```
⭕ git clone https://gitee.com/macos2/HBPLv1.0-Printer-driver
⭕ cd HBPLv1.0-Printer-driver/
⭕ ./configure 
Special The Install Path:[leave blank for /usr]

Install Path:/usr
⭕ make
Building foo2hbpl1
/usr/bin/ld: 找不到 -ljbig
collect2: error: ld returned 1 exit status
make: *** [makefile:5：foo2hbpl1] 错误 1
⭕ pfile libjbig.so
libjbig0:amd64: /usr/lib/x86_64-linux-gnu/libjbig.so.0
libjbig0:i386: /usr/lib/i386-linux-gnu/libjbig.so.0
⭕ pf libjbig*
正在列表... 完成
libjbig-dev/focal 2.1-3.1build1 amd64
libjbig-dev/focal 2.1-3.1build1 i386
libjbig0/focal,now 2.1-3.1build1 amd64 [已安装]
libjbig0/focal,now 2.1-3.1build1 i386 [已安装，自动]
libjbig2dec0-dev/focal 0.18-1ubuntu1 amd64
libjbig2dec0-dev/focal 0.18-1ubuntu1 i386
libjbig2dec0/focal,now 0.18-1ubuntu1 amd64 [已安装，自动]
libjbig2dec0/focal 0.18-1ubuntu1 i386
libjbigi-jni/focal 0.9.44-3 amd64
⭕ pi libjbig-dev
⭕ make
Building foo2hbpl1
Building hbpldecode
Building foo2hbpl1-wrapper
⭕ sudo make install
Install to /usr
Install icm&crd file
Install ppd file
⭕ g ppd makefile
install:all $(shell find crd/*.ps crd/*cms2 crd/*cms) $(shell find ppd/*.ppd)
	@mkdir -p $(INSTALL_DIR)/share/ppd/hbplv1
	@echo "\e[1;34mInstall ppd file\e[0m"
	@cp ppd/* $(INSTALL_DIR)/share/ppd/hbplv1
	@chmod 0644 $(INSTALL_DIR)/share/ppd/hbplv1/*.ppd
	@echo "\e[1;34mUnInstall ppd file\e[0m"
	@rm -r -f $(INSTALL_DIR)/share/ppd/hbplv1
⭕ l /usr/share/ppd/hbplv1/
Dell-1250c-foo2hbpl1.ppd  Epson-AcuLaser_C1700-foo2hbpl1.ppd
Dell-C1660-foo2hbpl1.ppd  Fuji_Xerox-DocuPrint_CP105-foo2hbpl1.ppd
Dell-C1760-foo2hbpl1.ppd  Generic_HBPLv1-foo2hbpl1.ppd
```

## cli 测试
```
⭕ foo2hbpl1-wrapper  <print.pdf >print.hbp1
⭕ sudo su
🔴 cat print.hbp1 >/dev/usb/lp1 

```

## 要点
一定要设置好`A4`纸张，缺省Letter纸张，会连续打3页📃📃📃。还要设置`彩色`输出，缺省单色。
