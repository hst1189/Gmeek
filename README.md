**简体中文** | **[English](README-en.md)** | **[Русский](README-ru.md)**
# Gmeek

一个博客框架，超轻量级个人博客模板。完全基于`Github Pages` 、 `Github Issues` 和 `Github Actions`。

不需额外部署，从搭建到写作，只需要18秒，2步搭建好博客。

- [Demo](http://hst1189.github.io/)
- [Gmeek版本](https://meekdai.github.io/post/Gmeek-geng-xin-ri-zhi.html)
- [Gmeek构建网站（基础篇）](http://hst1189.github.io/post/Vol.1%20Gmeek-gou-jian-wang-zhan-%EF%BC%88-ji-chu-pian-%EF%BC%89.html#google_vignette)
- [Gmeek构建网站（进阶篇）](http://hst1189.github.io/post/Vol.2%20Gmeek-gou-jian-wang-zhan-%EF%BC%88-jin-jie-pian-%EF%BC%89.html)

![light](img/light.jpg)

### 安装

1. 【创建仓库】点击[通过模板创建仓库](https://github.com/new?template_name=Gmeek-template&template_owner=Meekdai)，建议仓库名称为`XXX.github.io`，其中`XXX`为你的github用户名。

2. 【启用Pages】在仓库的`Settings`中`Pages`->`Build and deployment`->`Source`下面选择`Github Actions`。

> [!NOTE]
> 在默认情况下，`Github Actions`是调用 `Meekdai/Gmeek` 远端程序
> 如想回避，可以将本驱动本体 `Fork`在自己帐下，只需修改 `Github Action`文件即可`(.github/workflows/Gmeek.yml)`

  ```
        - name: Clone source code
        run: |
          GMEEK_VERSION=$(jq -r ".GMEEK_VERSION" config.json)
          git clone https://github.com/Meekdai/Gmeek.git /opt/Gmeek;
          cd /opt/Gmeek/
          lastTag=$(git describe --tags `git rev-list --tags --max-count=1`)
          if [ $GMEEK_VERSION == 'last' ]; then git checkout $lastTag; else git checkout $GMEEK_VERSION; fi;
  ```
  　　↓
  ```
        - name: Clone source code
        run: |
          GMEEK_VERSION=$(jq -r ".GMEEK_VERSION" config.json)
          git clone https://github.com/hst1189/Gmeek.git /opt/Gmeek;
          cd /opt/Gmeek/
  
  　　　　※fork时如果没有clone tag，找不到tag会报错，将最后2行删除即可 （缺点：版本将无法选择，默认取得main下最新）
  ```


3. 【开始写作】打开一篇issue，开始写作，并且**必须**添加一个`标签Label`（至少添加一个），再保存issue后会自动创建博客内容，片刻后可通过https://XXX.github.io 访问（可进入Actions页面查看构建进度）。

4. 【手动全局生成】这个步骤只有在修改`config.json`文件或者出现奇怪问题的时候，通过`Actions`->`build Gmeek`->`Run workflow`->里面的按钮全局重新生成一次


### 提交问题

1. 如果有问题可参考[Gmeek构建网站（基础篇）](http://hst1189.github.io/post/Vol.1%20Gmeek-gou-jian-wang-zhan-%EF%BC%88-ji-chu-pian-%EF%BC%89.html#google_vignette) 
2. 提交[Issues](https://github.com/Meekdai/Gmeek/issues)咨询

### 特性

- UI界面和Github同源，只引入了Github原生CSS：[primer.style](https://primer.style/css)
- 博客写作在Issues中完成后，自动触发Actions执行部署任务
- 评论系统引入[utteranc.es](https://utteranc.es/)
- 使用`jinja2`对html进行渲染，可通过模板自定义UI主题

### 赞赏


### 鸣谢
- [jinja2](https://jinja.palletsprojects.com/)
- [utteranc.es](https://utteranc.es/)
- [primer.style](https://primer.style/css)
- [gitblog](https://github.com/yihong0618/gitblog)

### License
请保留页面底部和console界面版权信息，谢谢！

