《学习GNU Emacs (第二版)》[美]卡马伦著 机械工业出版社 ISBN 978-7111103486





**软件布局**
**快捷键**
文件操作

>C+x C+f 打开文件
>C+x C+s 保存文件

光标移动

>

复制粘贴

>

**使用技巧（形成的使用习惯，一般这样使用）**
**缺点（需要注意的地方，避开坑，不要这样使用）**





总结，编辑器



**英文词汇**







**链接地址**
1.[Emacs For Mac OS X](https://emacsformacosx.com)
2.[Mac OS安装emacs](https://blog.csdn.net/SCHOLAR_II/article/details/80976314)
3.[一年内成为emacs高手](https://blog.csdn.net/redguardtoo/article/details/7222501)









解决emacs自动产生备份文件的烦恼

给  ~/.emacs 文件末尾添加两行代码

```shell
;; all backups goto ~/.backups instead in the current directory
(setq backup-directory-alist (quote (("." . "~/.backups"))))
```

