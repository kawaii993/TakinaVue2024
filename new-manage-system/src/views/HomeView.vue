<template>
  <div>
    <el-container>

      <!-- 侧边栏 -->
      <el-aside style="width: 200px; min-height: 100vh; background-color: rgba(68, 66, 99, 0.7) ;">
        <div style="height: 60px; line-height: 60px;  color: white; 
        display: flex; align-items: center; justify-content: center;">
          logo
        </div>
        <!-- 菜单栏 -->
        <el-menu router background-color="rgba(68, 66, 99, 0.3)" text-color="#fad0c4 " active-text-color="#ffd1ff "
          style="border: none;" :default-active="$route.path">
          <el-menu-item index="/">
            <template slot="title">
              <i class="el-icon-house"></i>
              <span>系统首页</span>
            </template>
          </el-menu-item>
          <el-menu-item index="element">Element页面</el-menu-item>
          <el-menu-item>系统首页</el-menu-item>
          <el-menu-item>系统首页</el-menu-item>
          <el-submenu>
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span>信息管理</span>
            </template>
            <el-menu-item>用户信息</el-menu-item>
            <el-menu-item>管理员信息</el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>


      <el-container>
        <!-- 头部区域 -->
        <el-header>
          头部区域
        </el-header>

        <!-- 主体区域 -->
        <el-main>
          主体区域
        </el-main>

      </el-container>

    </el-container>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'HomeView',
}
</script>

<style>

.el-menu--inline .el-menu-item{
  background-color: rgb(122, 113, 133) !important;
}
.el-menu-item:hover,el-submenu__title:hover{
  color: rgb(5, 39, 3) !important;
}
.el-submenu__title:hover i{
  color: #fff !important;
}
</style>