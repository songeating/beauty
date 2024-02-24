# Beauty

<https://songeating.github.io/beauty>

## 起因

<https://fulitu.me>上有许多写真，但每页只显示三张图片，且有很多广告。
于是我用Python写了个脚本，批量下载一个图集中的图片。
截止到本次commit，共有73个图集，3865张图片（如果我没搞错的话）。
由此也有了部署到GitHub Pages的想法，于是又写了个Python脚本，生成html文件。

由于没怎么学过html，Python也没学过多少，代码大多是现查现学的，
所以网页写的并不美观，脚本也有一些问题，还请大佬喷的时候嘴下留情。

## 关于图片

只选取了符合我xp的图片，不一定符合你的。
（我的xp大致是：jk制服，贫乳，白丝，白丝，白丝）

图集的名称是<https://fulitu.me>上的原名，未做修改。个别图集名与实际内容并不相符。

## 关于Python脚本

如果你需要使用我写的脚本，那么这是一个说明。

### 安装依赖：

```bash
pip install requests beautifulsoup4
```

### flt.py

`flt.py`用于从<https://fulitu.me>下载一个图集中的全部图片。
由于我在Android上使用Termux运行，`save_dir`设置为`"/sdcard/Download/flt/"`。
请根据你的实际情况修改保存目录。

进入<https://fulitu.me>上的一个图集，复制其第一页的网址，运行命令：

```bash
python flt.py <复制的网址>
```

将开始递归下载每一页的图片，并保存在`${save_dir}/<图集名称>`下。

如果你进入其他页码，请切换回第一页，否则先前页码的图片将不会被下载。

### gflt.py

`gflt.py`用于为每个图集生成部署到GitHub Pages的html文件。
请将`USERNAME`和`REPO`修改为你自己的，将`base`修改为存放图集文件夹的目录，相当于`flt.py`中的`save_dir`。
然后直接运行命令：

```bash
python gflt.py
```

生成的html中的img会使用<https://mirror.ghproxy.com>代理以加速中国大陆地区访问。

### 已知的问题

`flt.py`下载图片时，每一页的第一张图片会下载两次。
但<https://fulitu.me>确实把每一页的第一张图片的img标签重复写了两遍，所以这并不是脚本的问题。

`flt.py`和`gflt.py`在创建文件夹时，
如果已有同名文件，将会报错，因为我并没有加入存在检测。
所以如果在下载中途中断，需要删除整个图集文件夹再重新下载；
每次生成html文件前也需要将原有的文件夹全部删除。

如果你有能力，我还是建议你自己写。这两个脚本只是我为解决临时需求现学现写的。