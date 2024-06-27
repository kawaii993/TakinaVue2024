<template>
  <div>
    <el-container>

      <!-- 侧边栏 -->
      <el-aside :width="asideWidth" style=" min-height: 100vh; background-color: rgba(68, 66, 99, 0.5) ;">
        <div style="height: 60px; line-height: 60px;  color: white; 
        display: flex; align-items: center; justify-content: center;">
          logo
        </div>
        <!-- 菜单栏 -->
        <el-menu :collapse="isCollapse" :collapse-transition="false" router background-color="rgba(68, 66, 99, 0.3 )"
          text-color="#fad0c4 " active-text-color="#ffd1ff " style="border: none;" :default-active="$route.path">
          <el-menu-item index="/">
            <i class="el-icon-house"></i>
            <span slot="title">系统首页</span>
          </el-menu-item>

          <el-menu-item index="element">
            <i class="el-icon-eleme"></i>
            <span slot="title">Element页面</span>
          </el-menu-item>

          <el-menu-item index="/1">
            <i class="el-icon-house"></i>
            <span slot="title">系统首页</span>
          </el-menu-item>

          <el-menu-item index="/2">
            <i class="el-icon-house"></i>
            <span slot="title">系统首页</span>
          </el-menu-item>


          <el-submenu index="3">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span>信息管理</span>
            </template>
            <el-menu-item>用户信息</el-menu-item>
            <el-menu-item>管理员信息</el-menu-item>
            <el-menu-item index="/">系统首页</el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>


      <el-container>
        <!-- 头部区域 -->
        <el-header>
          <i class="el-icon-set-up " style="width: 40px; margin-top: 30px;font-size: 30px;" @click="handleCollapse">
          </i>
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
  data() {
    return {
      isCollapse: false,//不收缩
      asideWidth: '200px'
    }
  },
  methods: {
    handleCollapse() {
      this.isCollapse = !this.isCollapse
      this.asideWidth = this.isCollapse ? '64px' : '200px'
    }
  }
}
</script>

<style>
.el-menu--inline {
  background-color: rgb(122, 113, 133) !important;
}

.el-menu--inline .el-menu-item {
  background-color: rgb(122, 113, 133) !important;
  padding-left: 49px !important;
}

.el-menu-item:hover,
el-submenu__title:hover {
  color: rgb(5, 39, 3) !important;
}

.el-submenu__title:hover i {
  color: #fff !important;
}

.el-menu-item.is-active {
  background-color: #691b52 !important;
  border-radius: 10px !important;
  /* margin-left: 4px;
  margin-right: 4px;
  margin-top: 4px;
  margin-bottom: 4px; */
  /* margin: 4px; */
  width: calc(100%-8px);
  margin-left: 4px;
}

.el-menu-item.is-active i,
.el-menu-item.is-active .el-tooltip {
  margin-left: -4px;
}

.el-menu-item {
  height: 45px !important;
  line-height: 45px !important;

}

.el-submenu__title {
  height: 45px !important;
  line-height: 45px !important;

}

.el-submenu .el-menu-item {
  min-width: 0 !important;
}

.el-menu--inline .el-menu-item.is-active {
  padding-left: 45px !important;
}

/* .el-submenu__icon-arrow{
  margin-top: -5px;
} */
</style>