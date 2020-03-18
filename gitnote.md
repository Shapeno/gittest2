 

[一篇文章，教你学会Git](https://www.jianshu.com/p/072587b47515)：基础操作
[一篇文章搞定Git——Git代码管理及使用规范](https://blog.csdn.net/weixin_42092278/article/details/90448721)：规范

## **Git commit** 

**1.1 git commit -m “message”**

​      这种是比较常见的用法，-m 参数表示可以直接输入后面的“message”，如果不加 -m参数，那么是不能直接输入message的，而是会调用一个编辑器一般是vim来让你输入这个message，

　　　message即是我们用来简要说明这次提交的语句。还有另外一种方法，当我们想要提交的message很长或者我们想描述的更清楚更简洁明了一点，我们可以使用这样的格式，如下：

​    git commit -m ‘

​    message1

​    message2

​    message3

​    ’

  **1.2 git commit -a -m “massage”**

​      其他功能如-m参数，加的-a参数可以将所有已跟踪文件中的执行修改或删除操作的文件都提交到本地仓库，即使它们没有经过git add添加到暂存区，注意，

　　　新加的文件（即没有被git系统管理的文件）是不能被提交到本地仓库的。建议一般不要使用-a参数，正常的提交还是使用git add先将要改动的文件添加到暂存区，再用git commit 提交到本地版本库。

  **1.3 git commit --amend**

​      如果我们不小心提交了一版我们不满意的代码，并且给它推送到服务器了，在代码没被merge之前我们希望再修改一版满意的，而如果我们不想在服务器上abondon，那么我们怎么做呢？

​     git commit --amend //也叫追加提交，它可以在不增加一个新的commit-id的情况下将新修改的代码追加到前一次的commit-id中，

**1.4 git commit --help**

​    查看帮助，还有许多参数有其他效果，一般来说了解上述三种即可满足我们工作中的日常开发了

## Git tag 

###### 打标签

```css
git tag -a 0.1.3 -m “Release version 0.1.3″
```

###### 详解：

```css
git tag 是命令
-a 0.1.3是增加 名为0.1.3的标签
-m 后面跟着的是标签的注释
```

打标签的操作发生在我们commit修改到本地仓库之后。

##### 相关操作

###### 提交

```css
git add .
git commit -m “fixed some bugs”
git tag -a 0.1.3 -m “Release version 0.1.3″
```

###### 分享提交标签到远程服务器上

```undefined
git push origin master
git push origin --tags
```

–tags参数表示提交所有tag至服务器端，普通的git push origin master操作不会推送标签到服务器端。

###### 切换到已有Tag

```cpp
git tag --list  // 查看已有tag列表
git checkout [tag/branch/commit]  // 切换到指定tag/branch/commit都是此命令
```

###### 删除标签的命令

```css
git tag -d 0.1.3
```

###### 删除远端服务器的标签

```ruby
git push origin :refs/tags/0.1.3
```