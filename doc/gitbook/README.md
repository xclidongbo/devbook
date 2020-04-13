# gitbook简介

# gitBook文档
[GitBook文档](https://docs.gitbook.com/)
[GitBook开发手册](https://www.cntofu.com/book/76/index.html)

# gitbook创建

> gitbook-cli和gitbook是两个命令


```
npm install gitbook-cli -g
```
`git init`创建文件:

1. README.md(默认)
2. SUMMARY.md(文件的目录)

# 文档书写
创建`book.json`文件,指定readme文件的位置.

```
{
    "title": "我的一本书",
    "author" : "李东波",
    "description" : "我第一本书的描述，很好",
    "language" : "zh-hans",
    "structure": {
        "readme": "README.md"
    }
}
```

# 封面

封面由 cover.jpg 文件指定，cover_small.jpg 同样可以作为小版本封面存在。封面应该是 JPEG 格式的文件。

||大|小|
|-|-|-|
|文件|`cover.jpg`|`cover_small.jpg`|
|大小(像素)|1800\*2360|200\*262|

# pdf/epub/mobi格式
- [calibre](https://calibre-ebook.com/download_osx)

mobi格式,执行
```
gitbook mobi .
```
# 左侧导航栏添加链接信息

```
"links" : {
    "sidebar" : {
        "Home" : "http://zhangjikai.com"
    }
}
```


# 自定义页面样式

```
"styles": {
    "website": "styles/website.css",
    "ebook": "styles/ebook.css",
    "pdf": "styles/pdf.css",
    "mobi": "styles/mobi.css",
    "epub": "styles/epub.css"
}
```

# 插件

## 配置使用插件

```
"plugins": [
    "disqus"
]
```
然后使用`gitbook install`来安装新插件

## 去除自带插件
```
"plugins": [
    "-search"
]
```
## 配置插件属性

```
"pluginsConfig": {
    "fontsettings": {
        "theme": "sepia",
        "family": "serif",
        "size":  1
    }
}
```
# structure

指定 Readme、Summary、Glossary 和 Languages 对应的文件名，下面是这几个文件对应变量以及默认值：
|变量|含义和默认值|
|-|-|
|structure.readme|Readme file name (defaults to README.md)|
|structure.summary	|Summary file name (defaults to SUMMARY.md)|
|structure.glossary	|Glossary file name (defaults to GLOSSARY.md)|
|structure.languages	|Languages file name (defaults to LANGS.md)|

