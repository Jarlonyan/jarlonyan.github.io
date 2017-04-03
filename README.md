
# Fork 指南

我的个人博客：<https://jarlonyan.github.io>，欢迎 Star 和 Fork。按照下面的步骤，从零开始在github上搭建你自己的jekyll博客。


## 1. 入门。

   从你的Github上用git把刚刚生成好的 `yourusername.github.io` 项目clone下来，假设放在一个叫myblog的目录中。（在你的项目的右上角点击 `clone or download` 得到SSH的地址）
   ```
   git clone git@github.com:用户名/用户名.github.io.git myblog/
   ```
   
   到项目目录中，把除了 `.git/` 之外的其他文件夹全删了,（没错，一点不留，全删）。
   然后将我的博客项目拷贝下来，解压缩到myblog中，删除该项目中的 `.git/` ，其他文件保留。
   
## 2. 修改域名。

   如果你需要绑定自己的域名，那么修改 CNAME 文件的内容；如果不需要绑定自己的域名，那么删掉 CNAME 文件。

## 3. 修改配置。

   网站的配置基本都集中在 `myblog/_config.yml` 文件中，将其中与个人信息相关的部分替换成你自己的，比如网站的 title、subtitle 和 Disqus 的用户名等。

   **注意：** 因为 Disqus 处理用户名与域名白名单的策略存在缺陷，请一定将 `disqus\_username` 修改成你自己的。

## 4. 删除我的文章与图片。

   如下文件夹中除了 template.md 文件外，都可以全部删除，然后添加你自己的内容。

   * `myblog/_posts` 文件夹中是已发布的博客文章。
   * `myblog/_drafts` 文件夹中是尚未发布的博客文章。
   * `myblog/_wiki` 文件夹中我已发布的 wiki 页面。
   * `myblog/images` 文件夹中是文章和页面里使用的图片。

## 5. 修改「关于」页面。

   `pages/about.md` 文件内容对应网站的「关于」页面，里面的内容多为个人相关，将它们替换成你自己的信息，包括 \_data 目录下的 skills.yml 和 social.yml 文件里的数据。

## 6. 编辑你自己的博文，然后上传

    在 `myblog/_posts` 中编辑你自己的博文，文件形式为markdown格式。然后跳转到项目的根目录，使用下面的命令上传：

```
    git add .
    git commit -m "first commit"
    git push origin master  
```

## 7. 使用MathJax显示Latex公式

    编辑`myblog/_config.yml` 文件,更改 `markdown: kramdown` ，然后请要显示公式的***.html文件的head中添加：

```
<!--MathJax的配置脚本，用于临时简单的配置 -->
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    extensions: ["tex2jax.js"],
    <!--输入Latex公式，以HTML和CSS的形式显示输出 -->
    jax: ["input/TeX", "output/HTML-CSS"],
    tex2jax: {
      <!--$表示行内元素，$$表示块状元素 -->
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
      processEscapes: true
    },
    "HTML-CSS": { availableFonts: ["TeX"] }
  });
</script>
<!--加载MathJax的最新文件， async表示异步加载进来 -->
<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js">
</script>
```


## 8. 致谢

本博客外观基于 [码志](http://mazhuang.org) 修改，感谢！

此外，参考  [Github+Jekyll指南](http://playingfingers.com/2016/03/26/build-a-blog/)  和 [从零开始折腾Jekyll
——使用Jekyll模板](http://bluebiu.com/blog/learn-to-use-jekyll.html#fn:note_3) 可以迅速入门。

