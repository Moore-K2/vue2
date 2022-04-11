<template>
  <!-- 3 创建中间外部容器 -->
  <div class="banner-wrapper w">
    <div class="banner clearfix">
      <!-- 轮播图 -->
      <ul class="img-list">
        <li>
          <a href="javascript:;"><img src="../assets/img/1.png" alt="" /></a>
        </li>
        <li>
          <a href="javascript:;"><img src="../assets/img/1.png" alt="" /></a>
        </li>
        <li>
          <a href="javascript:;"><img src="../assets/img/1.png" alt="" /></a>
        </li>
        <li>
          <a href="javascript:;"><img src="../assets/img/1.png" alt="" /></a>
        </li>
        <li>
          <a href="javascript:;"><img src="../assets/img/1.png" alt="" /></a>
        </li>
      </ul>
      <!-- pointer -->
      <div class="pointer">
        <a class="active" href="javascript:;"></a>
        <a href="javascript:;"></a>
        <a href="javascript:;"></a>
        <a href="javascript:;"></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Banner",
};
</script>

<style>
/* 设置中间content容器 */

.banner-wrapper {
  /* background-color: #bfa; */
  height: 420px;
}

.banner img {
  width: 100%;
  /* 让图片对齐 */
  vertical-align: top;
  margin-top: -1px;
}

.banner {
  /* 给img-list li 和pointer充当参照物 ，
        这儿因为pointer要参照定位，所以要加height，否则高度要塌陷*/
  position: relative;
  height: 460px;
}

.banner .img-list li {
  /* 脱离文档流，让图片重叠在一起 */
  position: absolute;
}
/* 设置pointer */

.banner .pointer {
  position: absolute;
  bottom: 15px;
  right: 10px;
}

.pointer a {
  float: left;
  width: 10px;
  height: 10px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  margin: 0 3px;
  border: 1px solid rgb(0, 0, 0);
  /* box-shadow: 0 0 2px rgba(0, 0, 0, .5); */
}

.pointer a:hover,
.pointer .active {
  background-color: rgb(0, 0, 0);
  border: 1px solid rgba(255, 255, 255, 0.5);
}
/* 设置右边粘滞定位导航条 */

.nav-right {
  width: 30px;
  height: 200px;
  position: fixed;
  background-color: #e0dedc;
  /* 画布定位 */
  /* 视口宽度 = 
        left + margin-left + width + margin-right +right 
        auto + 0 + 30 + 643px + 50% = 视口宽度*/
  bottom: 60px;
  right: 50%;
  margin-right: -643px;
}
/* 设置粘滞定位 */

.nav-right li i {
  color: black;
  display: block;
  height: 40px;
  line-height: 40px;
  margin-left: 5px;
  font-size: 14px;
}
/* 广告位 */

.banner-wrapper {
  position: relative;
}

.ad-wrapper {
  /* 我也不知道这儿为啥有些内容要被上面覆盖，只能调整padding */
  padding-top: 40px;
  /* background-color: #bfa */
  height: 170px;
}

.shortcut {
  height: 170px;
  width: 234px;
  background-color: #5f5750;
  margin-right: 14px;
  margin-top: 14px;
}
/* 设置左侧字体和图标字体 */

.shortcut a {
  display: block;
  height: 84px;
  width: 76px;
  color: #e0dedc;
  text-align: center;
  overflow: hidden;
}

.shortcut a i {
  display: block;
  margin-top: 15px;
  margin-bottom: 10px;
  font-size: 16px;
}
/* 设置hover */

.shortcut a:hover {
  color: #fff;
}

.shortcut li,
.ad-img li,
.ad-wrapper ul {
  float: left;
}

.ad-wrapper .ad-img li {
  width: 316px;
  margin-right: 14px;
  margin-top: 14px;
}

.ad-wrapper .ad-img li:last-child {
  margin-right: 0px;
  margin-top: 14px;
}

.ad-wrapper .ad-img img {
  width: 100%;
  vertical-align: top;
}
</style>