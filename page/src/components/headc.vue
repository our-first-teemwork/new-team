<template>
  <div class="headc">
  <div class="header">
      <div class="head-wrapper">
        
        <span style=""><h4>欢迎来到实验室管理系统！ </h4></span>
        <!-- <div class=""><span style=""><h4>基本版</h4></span></div>   -->
        <div>
        基本版
          <Divider type="vertical" />
          <a href="#">手机版</a>
          <Divider type="vertical" />
          <a href="#">企业邮箱</a>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'headc',
}
</script>

<style>
.head-wrapper{
  position: fixed;
  top:0;
  width: 100%;
  height: 48px;
  z-index: 200;
  background-color:#f1f1f1;
  display: flex;
  align-items: center;
  justify-content:space-around;
}

</style>
