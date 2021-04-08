# 很菜鸡，图个方便没啥技术含量QAQ

```js
var myPlayer = videojs('myvideo');
videojs("myvideo").ready(function () {
    var myPlayer = this;
    this.on('pause', function () {
        clearInterval(interval);
        clearInterval(intervalStudyTime);
    });
    //视频播放结束
    this.on('ended', function () {
        $.alert("自动保存成功！");
        saveData();
    });
});
```

以后技术上来了可以再多写点功能！！！！:yum:

