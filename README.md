### 安装运行环境

访问[Ruby](http://railsinstaller.org/en)官网,下载安装Ruby安装包，并确保安装的Ruby版本在2.1.0以上。

安装Bundler

```
gem install bundler
```

### 发布博文

在你的博客的GitHub代码库页面里，点开_posts文件夹，这里面就是你的博客文章。

这些文章使用的格式是Markdown，文件后缀名是md，这是一种非常简单易用的有格式文本标记语言。

在发布博文前，你需要在文章的头部添加这样的内容，包括你的文章标题，发布日期，文章归类，和标签等。

    ---
    title: 标题
    date: 日期
    categories:
    - document
    tags:
    - document
    comments: true
    ---

完成后，保存为.md文件，文件名是date-标题，然后上传到_posts文件夹，commit，很快就可以在博客上看到新文章了。

### 本地构建

```
bundle install
bundle exec jekyll server
```