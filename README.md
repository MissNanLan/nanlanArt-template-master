# nanlanArt-template-master
一个用媒体查询写的很简单的响应式网站

![手机显示.png](https://upload-images.jianshu.io/upload_images/4092152-b0154b8449d315cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![手机显示.png](https://upload-images.jianshu.io/upload_images/4092152-92ebbc1b3675f4e0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![pad显示.png](https://upload-images.jianshu.io/upload_images/4092152-0f4f41f049a0fa2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![电脑显示.png](https://upload-images.jianshu.io/upload_images/4092152-31fdfc5133f2c58d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

核心代码,当然是媒体查询了,
css代码
```
@media screen and (max-width: 481px) { // 手机端的判定
  .container{
    .main-area{
      .item {
        width: 100% !important;
        min-width: 100px !important;
        margin: auto !important;
      }
    }
  }  
   .sidebar {
    z-index: 999;
    left: -249px;
  }
  .container .menu {
    display: block ;
  }
  .container .main{
    margin-left: 0;
  }
}

@media screen and (min-width: 481px) {
  .container .sidebar  {
    left: 0;
  }
}
@media screen and (min-width: 482px) and (max-width: 789px) {  // 平板
  .main .main-area .item {
    width: 90%;
  }

}
@media screen and (min-width: 790px) and (max-width: 1039px) {   // 平板
  .main .main-area .item  {
    width: 43%;
  }
}
@media screen and (min-width: 1040px) and (max-width: 1920px) { // pc
  .main .main-area .item {
    width: 20%;
  }
}
```
js代码
```
// 点击按钮事件
      oMenu.onclick = function() {
          if (oLeftBar.offsetLeft == 0) {
              oLeftBar.style.left = -249 + 'px';
          }
          else {
              oLeftBar.style.left = 0;
          }
      }


      // 监听页面宽度变化
      window.onresize = function() { // 实现响应式的关键代码
          judgeWidth();
      };

      // 判断页面宽度
      function judgeWidth() {
          if (document.documentElement.clientWidth > 481) {
              oLeftBar.style.left = 0;
          } else {
              oLeftBar.style.left = -249 + 'px';
          }
      }
// 返回顶部按钮的代码
      $(window).scroll(function() { // 隐藏显示按钮
          if($(window).scrollTop() >= 200){
              $('#fixedBar').fadeIn(300);
          }else{
              $('#fixedBar').fadeOut(300);
          }
      });
      $('#fixedBar').click(function() {
          $('html,body').animate({scrollTop:'0px'},800);
      })
```
