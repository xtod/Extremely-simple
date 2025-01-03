# Extremely Simple

一款极致简洁的Hugo主题 

![Extremely Simple](https://raw.githubusercontent.com/xtod/Extremely-simple/refs/heads/main/images/screenshot.png "Extremely Simple")

## 特性

* 快速 (4kb CSS)
* 自动切换亮暗主题
* 响应式布局
* 内容优先，针对可读性进行排版优化
* RSS
* 支持数学公式(MathJax)
* 支持HTML标记

## 安装使用

```sh
cd hugo/themes
git clone https://github.com/xtod/Extremely-simple.git
```

具体使用可以参考`example`中示例站点

### 自定义菜单

In order to add/edit/delete entries from the main menu, you have to edit the `menu.toml` file inside `data` folder. Through that file you can define the structure of the menu. Take a look at the default configuration to get an idea of how it works and read on for a more comprehensive explanation.

The `menu.toml` file accepts the following fields:

- `entries` define a new unordered list that will contain menu entries
- each entry is a member of the TOML array `entries` in question
- each entry can have the following attributes:
    - `title`, which defines the text to render for this menu entry (**NB: you can also specify HTML!**)
    - `url`, which can be used to specify an URL for this entry. If not specified, `title` will be rendered as-is; otherwise `title` will be sorrounded by a link tag pointing to the specified URL. Note that the URL can either be relative or absolute. Also note that you can get the same result by placing an ```<a>``` tag in the `title` field.
    - `post_list`, which can be set either to `true` or to an object. If it is true, the entry will have a list of all posts as subentries. This is used to render your post list. If you want to customize which posts to render (e.g. by section), you can add one or more of the following attributes under `post_list`:
        - `section`, which can be set to a string. It is used to render a list of posts of the specified section only. If you don't set it, then posts of all sections will be rendered.
        - `limit`, which can be set to a number. It specifies the number of posts to show. If not set, all posts will be rendered.
        - `show_more`, which can be true. If it is true and if the number of posts to show is greater than the specified `limit`, render a link to another page. To specify the URL and the text of the link, you can set `show_more_url` and `show_more_text` attributes, which are documented below.
        - `show_more_url`, which can be a string. It specifies the URL for the show more link. Use only if `show_more` is true. This will usually redirect to a page containing all posts, which you can easily create using an section page (see [section pages](#section-pages) section)
        - `show_more_text`, which can be a string. It specifies the text for the show more link. Use only if `show_more` is true.
    - `entries`, yes, you can have entries inside entries. In this way you can create nested sublists!

### Section pages

A so-called section page is a page that shows a list of posts in a specific section. It should be automatically created by hugo when a new section is created.

### 自定义首页

The `index.md` page should use layout `home`, which is the layout that displays the menu. If you want to have some content after the menu, you can just add that content in the `_index.md` file, and it will automatically show under the menu.

Another thing you can do to customize the index page is show the description of your blog between the title and the menu. To do this, just edit `config.toml` and change `params.theme_config.show_description` to `true`.

You can also add footer. Just edit ..nostyleplease/layouts/footer.md.
### 添加目录

You can add a table of contents by supplying the `toc: true` param to your post front matter. If you want a border around it you can also set `tocBorder: true`. The toc style behavior is handled by Goldmark and the defaults can be found in the `config.toml` file.

### 文章列表按日期降序分组

编辑`hugo.yaml`将`params.theme_config.isListGroupByDate`修改为`true`。

### Pro tips

#### 深色模式图像

This theme provides dark mode by inverting all colors of light mode throught the CSS `invert()` function. This approach would also invert the color of all images, but, since this is not the behaviour one would expect, images are not inverted by default.

However, if you would like to force the color inversion on a specific image you can do so by applying `class="ioda"` to that image ("ioda" stands for "invert on dark appearance"). See the image in the [overview post](https://github.com/riggraz/no-style-please/blob/master/_posts/2020-07-07-overview-post.md) for an example of this approach. Note that color inversion will take place only when the theme has dark appearance!

For example, if you have a black and white image it could make sense to invert it in dark mode. On the other hand, a colorful image will probably look bad if inverted.


## 感谢

基于[riggraz/no-style-please](https://github.com/riggraz/no-style-please/)二次修改。

一些代码参考[wooseopkim/hugo-theme-nostyleplease](https://github.com/wooseopkim/hugo-theme-nostyleplease)。


## 许可

 [MIT License](https://opensource.org/licenses/MIT).