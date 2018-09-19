---
    title: 首次使用hexo搭建博客教程
---

## 前期工作准备

* 确认自己的git和npm已经安装。检查方式：
    1. win+R 输入cmd
    2. 输入npm -v 和 git --version
    3. 如显示安装，则无需操作。如显示未安装，自行百度安装。

## hexo下载
1. 新建文件夹并进入文件夹点击右键选中 Git bush here

2. 输入 npm install -g hexo-cli,静候佳音

    ![](../../../../css/images/error/tips1.png '描述')

3. 显示完成后再输入 hexo init, 静候佳音

    ![](../../../../css/images/error/tips2.png '描述')

4. 显示完成后再输入 npm install, 静候佳音

    ![](../../../../css/images/error/tips3.png '描述')

5. 此时已经全部准备就绪,输入命令行 hexo s,显示下图后在浏览器输入http://localhost:4000, 即可查看你的博客啦~

    ![](../../../../css/images/error/tips4.png '描述')

## 更换主题

* 只需一句代码便可更换主题成功

    ![](../../../../css/images/error/tips5.png '描述')

> 说明：①是你所看中主题的地址；②是你在themes文件夹里面放主题的文件夹

* 具体如图所示

    ![](../../../../css/images/error/tips6.png '描述')

* 更换成功后，先输入 hexo g再次渲染页面，再输入hexo s.