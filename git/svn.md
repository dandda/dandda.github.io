1. svn checkout url(这里输入服务器地址)
   > 表示从服务器拉取代码到本地。相当于 git clone.
2. svn mkdir https://172.24.104.100/svn/syfz_new-src/syfz_web -m '创建一个新文件夹'

   > 说明：svn mkdir 命令创建一个新文件夹。syfz_web 为新文件夹名称。在此之前该目录下没有 syfz_web 这个文件夹。`-m`注释内容。

3.svn add --force .

> 该命令是用于将代码添加到本地仓库。`force`表示可以添加所有新文件（未版本化）。`svn add filename`只能单个单个添加文件。

4.  svn commit -m '注释'

> 提交代码到服务器上。（相当于 git commit 和 git push）

参考：[svn 中文网](http://www.svn.org.cn/1099.html)
[git 和 SVN 常用操作 (mac 命令版)](http://pliangwei.com/details/34)
[svn 视频教学](https://www.bilibili.com/video/av66292191/)
[svn book](http://svnbook.red-bean.com/)
