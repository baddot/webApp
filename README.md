###项目文档

##### 项目在线地址

[在线地址](http://123.56.220.55)

##### webApp项目建立

* 四个页面分类(推荐,排行,路由,我的)
* 基本样式结构搭建  颜色暂定  rgb(105, 25, 51)
* 首页页 : 1.轮播图  2.搜索  3.歌手分类  4.歌曲分类  5.新歌速递  6.每日推荐
* 排行页 : 1.搜索   2.巅峰榜列表展示(各种类歌单的前三首展示)
* 歌单页 : 1.轮播图 2.全部歌单(其中一个歌单的全部整个列表图片+歌名)
* 我的页面 : 个人设置部分 (细节待定 暂为空)


##### 使用数据(数据为QQ音乐官方接口,仅供学习)

* 功能 :
* 跑通页面跳转路由 vue-router
* 没有使用原生ajax , 而是使用了vue-resource插件代替原生ajax进行接口调用
    + this.$http.get(url, ).then(function(response) { console.log(response) })
* 需要的数据 : 歌名 歌手名 图片 歌曲播放地址
* 列表渲染将数据渲染到页面  v-for
* 事件处理器 对被渲染在页面上的歌曲做操作  v-on

---

* 问题 :
* 引入插件报错问题



##### 样式修正

* 修复 :
* 由于之前引入的是自己写的一个功能类插件 代码中写入了大量的事件 不符合vue的事件处理机制 所以报错
* 修改页面结构样式
* 某些指定事件添加方法 给元素ref属性 在 生命周期methods 中写入执行代码

---

* 问题 :
* 一首歌曲播放结束后就会报错卡死
* 页面间的数据传递问题 需要将歌词的id传递到播放页面


##### 增加功能
* 新增
* 搜索部分功能
* 搜索列表展示下拉加载功能(每条10首歌)
* 通过获取id ,用此id请求歌曲的歌词 通过正则表达式处理lrc格式的歌词
* 歌词同步渲染到页面 通过歌词中的时间与当前播放时长的对应关系
* 增加loading样式 增强体验效果

* 修复
* 通过配置路由和点击事件的参数传递,另一个页面的数据接收问题解决
* 修改搜索模式 选中搜索框直接进入搜索页面 提高效率

##### 整体修改
* 修改
* 整体页面背景颜色修改
* 增加禁止缩放限制
* 增加移动端浏览器访问体验 移动端主流浏览器体验优化
* 增加各种机型适配样式 修复移动端部分样式错乱问题

---

* 问题与想法
* 整体背景修改后的部分样式不明显问题
* 懒加载问题
* 关于播放页面
    + 3个按钮在移动端显示的时候总感觉是歪的
    + 无播放列表 没有做切换歌曲的功能


##### 重构

* 安装 vue-awesome-swiper 插件 让4个主要导航滑动展示 增强体验
* 新增一个home页面  将4个页面配合vue-awesome-swiper 插件渲染到home页面 在通过路由渲染到入口页

##### 播放列表重建
* 思路
* 将进入方式从路由跳转转为展开隐藏在home页面中的元素 (好处是可以获取到更多的信息 不仅仅是歌曲id)
* 选择一首歌之后并不会直接进入大的播放页面 而是将歌曲添加到页面底部的播放栏中 当点击这个播放栏时 在展开整页的播放器

##### VueX的加入
* 使用vuex作为数据存储空间与多个组件间的通信功能
* 减少了路由跳转页面 变为组件与组件间的跳转
* 由于用到vuex中的辅助函数 需要用到es7的语法 下载相关babel解析包并重新配置.babelrc文件
* 页面结构变更 新增底部的播放器

##### 播放列表重建2
* 新增播放列表并配置列表功能 选中的歌曲添加至列表中可任意选择播放
* 底部播放器与整页单曲播放器的跳转
* 2个播放页面数据统一
* 光碟样式回归 并将光碟改为当前播放歌曲的封面
* 播放页背景为虚化的歌曲图片
* 上一首  下一首

##### 预知后事如何 请听下回分解
* 歌词改为只展示一句 显示在光碟的下面(暂定)
* 播放模式


##### 已知bug
* 播放页面css3滤镜属性UC浏览器不支持
* 无歌曲时底部播放栏应该隐藏
* 播放组件代码量过多 应该做拆分


## Start
+ npm install

## Develop
+ npm run dev

## Build
+ npm run build

##### 项目截图

![首页] (https://github.com/houbx/webApp/blob/master/screenshot/recommend.png)
![排行] (https://github.com/houbx/webApp/blob/master/screenshot/rank.png)
![播放] (https://github.com/houbx/webApp/blob/master/screenshot/play.png)
![搜索] (https://github.com/houbx/webApp/blob/master/screenshot/search.png)
