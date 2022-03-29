Tabs标签页

1、设置下划线的滑动时：记得设置绝对定位，以及他所处位置的相对定位。如：
.tabs .line{position: absolute;}
.tabs .tab-header{position: relative;}

2、document.querySelectorAll('.tabs').forEach($container => new Tabs($container)）
一次激活多个Tabs的内容设置，取代单独设置多个Tabs，如：
new Tabs(document.querySelectorAll('.tabs')[0])
new Tabs(document.querySelectorAll('.tabs')[1])
new Tabs(document.querySelectorAll('.tabs')[2])等
