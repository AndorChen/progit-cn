# 《精通 Git》：《Pro Git》中文版

生成电子书，包含 PDF、ePub 和 mobi 格式。

## 下载电子书

<https://selfstore.io/products/46>

## 开发者

1.  克隆仓库

    ```sh
    git clone https://github.com/AndorChen/progit-cn.git
    ```

2.  获取子模块

    ```sh
    git submodule init
    git submodule update
    ```

3.  安装 Rake

    ```sh
    bundle
    ```

4.  复制 Markdown 文件

    ```sh
    bundle exec rake copy:markdown [lang='zh']
    ```

5.  复制图片（基本上只需执行一次）

    ```sh
    bundle exec rake copy:figure
    ```

## 维护者

- [Andor Chen](http://about.ac)

## 发布协议

本书采用“[CC 署名-非商业性使用-相同方式共享 3.0 未本地化版本](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.zh)”协议发布。未经作者和译者允许，禁止用于商业用途。
