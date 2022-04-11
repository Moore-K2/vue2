<template>
  <!-- 设置顶部导航条 -->
  <!-- 1 顶部导航条外部容器 -->
  <div class="topbar-wrapper">
    <!-- 顶部导航栏内部容器 -->
    <div class="topbar w">
      <!-- 设置左边的一块 -->
      <ul class="service">
        <li><a href="javascript:;">小米商城</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">MIUI</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">loT</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">云服务</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">天星数科</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">有品</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">小爱开放平台</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">企业团购</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">资质证照</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">协议规则</a></li>
        <li class="line">|</li>
        <li class="download">
          <a class="app" href="javascript:;">
            下载app
            <i class="fas fa-caret-up"></i>
            <div class="qrcode">
              <img src="../assets/img/qrcode.png" alt="" />
              <br />
              <span>小米商城APP</span>
            </div>
          </a>
        </li>
        <li class="line">|</li>
        <li><a href="javascript:;">SelectLocation</a></li>
      </ul>
      <!-- 设置右边的两块 -->
      <ul class="shop-car">
        <li>
          <a href="javascript:;">
            <i class="fas fa-cart-plus"></i> 购物车 (0)
          </a>
          <div class="car">
            <span>购物车里还没有商品，赶紧选购吧!!</span>
          </div>
        </li>
      </ul>
      <ul class="user-info">
        <li><a href="javascript:;">登录</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">注册</a></li>
        <li class="line">|</li>
        <li><a href="javascript:;">消息通知</a></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopBar",
};
</script>

<style scoped>
</style>