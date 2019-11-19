# uni-app 问题回顾
## 1.scroll-view 无法横向排列
将scroll-view的子元素的class 设置为
```
display: inline-block;
```

## 2.自定义tabbar
 uni-app的tabbar最多支持5个页面，即使是自定义的，需要动态改变的tabbar，加起来也不能超过5个,需要在page.json文件进行设置, 如:
```
"tabBar": {
  "list": [{
    "pagePath": "pages/actualQuotation/ActualQuotation",
    "text": ""
  },{
    "pagePath": "pages/offer/Offer",
    "text": ""
  },{
    "pagePath": "pages/buy/Buy",
    "text": ""
  },{
    "pagePath": "pages/finance/FinancePage",
    "text": ""
  },{
    "pagePath": "pages/information/Information",
    "text": ""
  }]
}
```
自定义tabbar里最好使用 cover-view 和 cover-image 来创建视图

## 3.border为1rpx时在各个机型上的适配问题
### 可以在view里添加两倍的border视图再缩小一倍
```
<view class="a-view">
  <view class="a-border" />
</view>
...

<style>
.a-view{
  position: relative;
}
.a-border::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 200%;
  height: 200%;
  transform: scale(0.5);
  transform-origin: 0 0;
  box-sizing: border-box;
  border: 2rpx solid #6FBD1B;
}
</style>

```

## 4.页面滚动问题
```
  "disableScroll": true,  //true禁止滚动 false可以滚动
```

## 5.自定义tabbar相关问题
 按官方介绍 可以用cover-view来自定义tabbar，但是cover-view设置
```
position: fixed;
bottom: 0;
```
在iPhone上加载分页数据时会出现cover-view上移的bug, 目前方案为改cover-view为view，层级设置高一点, 如:
```
z-index: 999
```




