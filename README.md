# Editor.md

![](https://pandao.github.io/editor.md/images/logos/editormd-logo-180x180.png)

![](https://img.shields.io/github/stars/pandao/editor.md.svg)
![](https://img.shields.io/github/forks/pandao/editor.md.svg)
![](https://img.shields.io/github/tag/pandao/editor.md.svg)
![](https://img.shields.io/github/release/pandao/editor.md.svg)
![](https://img.shields.io/github/issues/pandao/editor.md.svg)
![](https://img.shields.io/bower/v/editor.md.svg)

**Editor.md** : The open source embeddable online markdown editor (component), based on CodeMirror & jQuery & Marked.

### 写在最前

   fork之后发现居然编译不了，然后看issue找到了另外一个仓库https://github.com/hawtim/editor.md，非常感谢，然后更新了一下下，然后顺便升级了一下marked库，表格最后一个为空时会消失的Bug修复了。  
   顺便参考了一下http://www.chairis.cn/blog/article/15 这篇文字，把代码复制了一下下，把粘贴图片也加上了，但是只能复制一张，多都不行，原因：未解之谜
   然后平时都有阿里的oss,顺便也加上了，因为oss的sdk好像只能在现代浏览器运行，所以不兼容了，粘贴也没兼容的，8012年了大哥。  
   http://www.chairis.cn/blog/article/15 这篇文字提到了一个前端压缩的库https://github.com/think2011/localResizeIMG，好像有bug,而且不更新了，如果遇到问题不要开就是了  
   
   以下是使用方法
   
   新增配置
   ```javascript
    resizeImageBeforeUpload: false,     // 上传图片前是否压缩
    resizeImageMaxWidth: 0,             // 图片最大不超过的宽度，默认为原图宽度，高度不设时会适应宽度。
    resizeImageMaxHeight: 0,            // 同上
    resizeImageQuality: 0.7,            // 图片压缩质量，取值 0 - 1，默认为0.7
    autoUploadPasteImage: false,        // imageUpload为true有效，自动上传粘贴的图片
    parseAjaxResponse: function (res) {	// 返回url 返回null标识上传失败
                if (res.status) {
                    return res.data.url;
                } else {
                    return null;
                }
    },
    ajaxUploadHeader: {},                // 上传头         粘贴用的
    ajaxUploadParams: {},                // 附带参数       粘贴用的
    ajaxUploadFileKey: "file",           // 上传参数名称    粘贴用的
    // 开启oss的话用按钮上传和粘贴都是上传到oss
	sts: "",                             // imageUpload为true有效，阿里OSS直连上传Token服务器地址，优先级高于imageUploadURL
    stsRequestHeaders: {},               // SecurityToken请求头
    stsRequestParams: {},                 // SecurityToken附带参数 例如{"token":"helloworld"}
    ossImageUploadFolder: "editormd/image",  // 非'/'开头和结尾
   ```  
   
   sts要返回的数据格式
   ```json
   {
       "data":{
           "code":"success",    
           "accessKeyId":"accessKeyId",
           "accessKeySecret":"accessKeySecret",
           "securityToken":"securityToken",
           "bucket":"bucket",
           "endpoint":"oss-cn-shenzhen.aliyuncs.com",
           "region":"cn-shenzhen",
           "expiration":"2018-10-26T10:42:19Z"
       },
       "status":true
   }
   ```

    
其他关于sts的请参考阿里云文档 https://help.aliyun.com/document_detail/31926.html?spm=a2c4g.11174283.6.643.1ddc7da2K8yvQP

以上

### Features

- Support Standard Markdown / CommonMark and GFM (GitHub Flavored Markdown);
- Full-featured: Real-time Preview, Image (cross-domain) upload, Preformatted text/Code blocks/Tables insert, Code fold, Search replace, Read only, Themes, Multi-languages, L18n, HTML entities, Code syntax highlighting...;
- Markdown Extras : Support [ToC (Table of Contents)](https://pandao.github.io/editor.md/examples/toc.html), [Emoji](https://pandao.github.io/editor.md/examples/emoji.html), [Task lists](https://pandao.github.io/editor.md/examples/task-lists.html), [@Links](https://pandao.github.io/editor.md/examples/@links.html)...;
- Compatible with all major browsers (IE8+), compatible Zepto.js and iPad;
- Support [decode & fliter of the HTML tags & attributes](https://pandao.github.io/editor.md/examples/html-tags-decode.html);
- Support [TeX (LaTeX expressions, Based on KaTeX)](https://pandao.github.io/editor.md/examples/katex.html), [Flowchart](https://pandao.github.io/editor.md/examples/flowchart.html) and [Sequence Diagram](https://pandao.github.io/editor.md/examples/sequence-diagram.html) of Markdown extended syntax;
- Support AMD/CMD (Require.js & Sea.js) Module Loader, and Custom/define editor plugins;

[README & Examples (English)](https://pandao.github.io/editor.md/en.html)
  

--------

**Editor.md** 是一款开源的、可嵌入的 Markdown 在线编辑器（组件），基于 CodeMirror、jQuery 和 Marked 构建。

![editormd-screenshot](https://pandao.github.io/editor.md/examples/images/editormd-screenshot.png "editormd-screenshot")

#### 主要特性

- 支持通用 Markdown / CommonMark 和 GFM (GitHub Flavored Markdown) 风格的语法，也可[变身为代码编辑器](https://pandao.github.io/editor.md/examples/change-mode.html)；
- 支持实时预览、图片（跨域）上传、预格式文本/代码/表格插入、代码折叠、跳转到行、搜索替换、只读模式、自定义样式主题和多语言语法高亮等功能；
- 支持 [ToC（Table of Contents）](https://pandao.github.io/editor.md/examples/toc.html)、[Emoji表情](https://pandao.github.io/editor.md/examples/emoji.html)、[Task lists](https://pandao.github.io/editor.md/examples/task-lists.html)、[@链接](https://pandao.github.io/editor.md/examples/@links.html)等 Markdown 扩展语法；
- 支持 TeX 科学公式（基于 [KaTeX](https://pandao.github.io/editor.md/examples/katex.html)）、流程图 [Flowchart](https://pandao.github.io/editor.md/examples/flowchart.html) 和 [时序图 Sequence Diagram](https://pandao.github.io/editor.md/examples/sequence-diagram.html);
- 支持[识别和解析 HTML 标签，并且支持自定义过滤标签及属性解析](https://pandao.github.io/editor.md/examples/html-tags-decode.html)，具有可靠的安全性和几乎无限的扩展性；
- 支持 AMD / CMD 模块化加载（支持 [Require.js](https://pandao.github.io/editor.md/examples/use-requirejs.html) & [Sea.js](https://pandao.github.io/editor.md/examples/use-seajs.html)），并且支持[自定义扩展插件](https://pandao.github.io/editor.md/examples/define-plugin.html)；
- 兼容主流的浏览器（IE8+）和 [Zepto.js](https://pandao.github.io/editor.md/examples/use-zepto.html)，且支持 iPad 等平板设备；

#### Examples

[https://pandao.github.io/editor.md/examples/index.html](https://pandao.github.io/editor.md/examples/index.html)

#### Download & install

[Github download](https://github.com/pandao/editor.md/archive/master.zip)

Bower install :

```shell
bower install editor.md
```

#### Usages

HTML：

```html
<link rel="stylesheet" href="editormd.min.css" />
<div id="editormd">
    <textarea style="display:none;">### Hello Editor.md !</textarea>
</div>
```

> Tip: Editor.md can auto append `<textarea>` tag;

javascript:

```html
<script src="jquery.min.js"></script>
<script src="editormd.min.js"></script>
<script type="text/javascript">
    $(function() {
        var editor = editormd("editormd", {
            path : "../lib/" // Autoload modules mode, codemirror, marked... dependents libs path
        });

        /*
        // or
        var editor = editormd({
            id   : "editormd",
            path : "../lib/"
        });
        */
    });
</script>
```

Using modular script loader :

- [Using Require.js](https://github.com/pandao/editor.md/tree/master/examples/use-requirejs.html)
- [Using Sea.js](https://github.com/pandao/editor.md/tree/master/examples/use-seajs.html)

#### Dependents

- [CodeMirror](http://codemirror.net/ "CodeMirror")
- [marked](https://github.com/chjj/marked "marked")
- [jQuery](http://jquery.com/ "jQuery")
- [FontAwesome](http://fontawesome.io/ "FontAwesome")
- [github-markdown.css](https://github.com/sindresorhus/github-markdown-css "github-markdown.css")
- [KaTeX](http://khan.github.io/KaTeX/ "KaTeX")
- [prettify.js](http://code.google.com/p/google-code-prettify/ "prettify.js")
- [Rephael.js](http://raphaeljs.com/ "Rephael.js")
- [flowchart.js](http://adrai.github.io/flowchart.js/ "flowchart.js")
- [sequence-diagram.js](http://bramp.github.io/js-sequence-diagrams/ "sequence-diagram.js")
- [Prefixes.scss](https://github.com/pandao/prefixes.scss "Prefixes.scss")

#### Changes

[Change logs](https://github.com/pandao/editor.md/blob/master/CHANGE.md)

#### License

The MIT License.

Copyright (c) 2015 Pandao
