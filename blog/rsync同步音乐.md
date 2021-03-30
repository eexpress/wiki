# 同步目录
---
## rsync 同步音乐目录

```
⭕ rsync -rn -i --delete  /media/eexpss/TF128G/音乐/ /media/eexpss/3461-3038/音乐
*deleting   tt
>f+++++++++ 04 - To Be Alone With You.flac
>f+++++++++ 张国荣-最爱.flac
>f+++++++++ 情人 - 刀郎.flac
>f+++++++++ 谭咏麟/一生中最爱_谭咏麟 - 李克勤.flac
>f+++++++++ 邓丽君/邓丽君 - 夜色.flac
>f+++++++++ 邓丽君/邓丽君&华语群星-夜色.wav
```

> *deleting 就是目标目录多出的文件。

参数说明|x|x
--|--|--
-i, --itemize-changes|       output a change-summary for all updates|用于输出这个列表信息。
-r, --recursive|             recurse into directories|递归目录
-n, --dry-run|               perform a trial run with no changes made|试运行
--delete|                delete extraneous files from dest dirs|删除目标目录多出的文件

> 第一个目录(directory1/)后一定不能缺少斜线，否则表示将directory1整个目录同步到directory2目录下。

> 假定了比较的两个目录中只有普通文件和目录，没有软链接、块设备等特殊文件。否则使用-a替代-r。

---

## meld比较目录
[x] meld首选项->文件夹比较->粗浅比较->**只按大小和时间戳比较文件**
> 不比较文件内容才能快速。
