banner
======

网易公开课banner横向切换效果


http://hi.baidu.com/tang_guangyao/item/c7c9dd574739a8fdd58bacc6


这个banner优点是在从第一张直接切换到第N张时，他中间没有2到N-1张的过度，而是无缝连接，没有那种banner图片走位很晃眼的感觉。

例如网址比较常见的一种简单的横向滚动：
http://www.16sucai.com/uploadfile/show4/jQueyjdt008/  （网上找的一个例子）
从第一张点到第4张时，中间经过图片太多。
这种的原理非常简单
<div>
    <ul>
       <li></li>
       <li></li>
       ...
    </ul>
</div>
原理就是这个ul长度是所有<li>之和，<div>等于<li>的长度切overfollow:hidden;


如上图，黄线部分是overfollow:hidden;
然后<ul>设置绝对定位，<div>设置相对定位，用js控制<ul>的left就能展现一个横向移动的效果；
当然，这个js写好了，写成非常通用的插件也是很难的。。。

然后重点说下网易公开课的那个js效果的原理：

如下图

图一

红色div在最外层，为可以显示的窗口，长度等于一个Li，同时也是overfollow:hidden;
蓝色div为红色下面的一层，长度等于3个Li长度；
和上面一个布局原理的差别是，上面的蓝色区域是更具LI个数决定的，这个只要是li>2测，蓝色<div>就等于3个LI长度；

具体切换效果是，当前显示Li在Li2位置，如果点击后面的图片，则后面的图片放置在Li3位置（原版隐藏的设置为显示），然后动画效果是，整个蓝色<div>左移动一个Li位移，


这个动画效果有个时间，例如1000毫秒，这样就有一个横向移动的效果，当这个动画效果完成后，
将Li2 设置为隐藏，蓝色<div>左移动一个Li位移，Li3移到Li2位置（也就是左移动一个Li）这时又回到图一 的样式。

当点击前面的图片是，是同样的原理，把点击图片放在Li1位置（原本隐藏的设置为显示），然后整个蓝色<div>动画效果又移动一个Li的距离，在动画效果完成后，隐藏移动走的Li2元素，将Li3移到Li2位置，蓝色<div>做移动一个Li返回原来位置。

这样就能达到，不管事点击当前图片后面或者前面的第几张图片，这张图片都是仅仅挨着当前图片横向滑动，没有中间的图片干扰。

另外我将整个网易banner切换效果扣了出来，而且在js上面标注了非常详细的注解：
如果上面原理没有看懂的可以直接看源代码理解

备注，这个js是网易工程师原作（版权归他），我仅做交流分享使用

下载地址（我使用的mac用软件压塑的文件，不知道window能不能打开）：

http://pan.baidu.com/share/link?shareid=6519&uk=52813371

这个插件集合了很多功能，这个横向移动是其中的一块



下面就是我自己根据这个原理写的一个js效果简化版

js banner切换横向滚动效果（简化版）
