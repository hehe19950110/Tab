Tabs标签页

1、设置下划线的滑动时：记得设置绝对定位，以及他所处位置的相对定位。
如：
```
.tabs .line{position: absolute;}
.tabs .tab-header{position: relative;}
```

2、this代表对象，代表即将要创建的实例；
但是内部如果有绑定事件，onclick里面的this变成了绑定事件里面的DOM元素，
如果仍需要使用this来获取实例，则需要先将this保存设置为其他的名字；
又或者将绑定事件内部 用箭头函数来代替。
如：
```
 bind(){
    let self = this
    this.$$tabItems.forEach($tab => {
      $tab.onclick = function() {
        self.$$tabItems.forEach($tab => $tab.classList.remove('active'))
        this.classList.add('active')

        self.$line.style.width = this.offsetWidth + 'px'
        self.$line.style.transform = `translateX(${this.offsetLeft}px)`

        let index = [...self.$$tabItems].indexOf(this)
        self.$$tabPanels.forEach($panel => $panel.classList.remove('active'))
        self.$$tabPanels[index].classList.add('active')
      }
```

3、需要一次性激活多个Tabs的内容设置，
```
document.querySelectorAll('.tabs').forEach($container => new Tabs($container)）
```
可取代单独分别设置多个Tabs，
如：
```
new Tabs(document.querySelectorAll('.tabs')[0])
new Tabs(document.querySelectorAll('.tabs')[1])
new Tabs(document.querySelectorAll('.tabs')[2])等
```
