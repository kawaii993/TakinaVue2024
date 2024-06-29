<template>
  <div>
    <el-container>

      <!-- 侧边栏 -->
      <el-aside :width="asideWidth" style=" min-height: 100vh; background-color: rgba(68, 66, 99, 0.9) ;">
        <div style="height: 60px; line-height: 60px;  color: white; 
        display: flex; align-items: center; justify-content: center;">
          <img src="@/assets/logo.png" alt="" style="width: 40px;height: 40px;">
          <transition name="el-fade-in-linear">
            <span style="margin-left: 5px; font-size: 20px;" v-show="!isCollapse">Cutey993</span>
          </transition>
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
            <el-menu-item>其他信息</el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>


      <el-container>
        <!-- 头部区域 -->
        <el-header>
          <i :class="collapseIcon" style="width: 40px; margin-left: 20px;margin-right: 20px;font-size: 26px;"
            @click="handleCollapse">
          </i>
          <el-breadcrumb separator-class="el-icon-arrow-right">
            <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
            <el-breadcrumb-item :to="{ path: '/element' }">Element页面</el-breadcrumb-item>
            <el-breadcrumb-item :to="{ path: '/user' }">用户管理</el-breadcrumb-item>
          </el-breadcrumb>

          <div style="flex: 1; width: 0; display: flex; align-items: center; justify-content: flex-end;">
            <i class="el-icon-quanping-copy" style="font-size: 24px;margin-right: 20px;" @click="handleFull"></i>
            <el-dropdown placement="bottom">
              <div style="display: flex; align-items: center; cursor: default;">
                <img src="@/assets/logo1.jpg" alt="" style="width: 40px; height: 40px;margin-right: 5px;">
                <span>眠羊</span>
              </div>

              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>个人信息</el-dropdown-item>
                <el-dropdown-item>修改密码</el-dropdown-item>
                <el-dropdown-item @click="1">退出登录</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </div>

        </el-header>

        <!-- 主体区域 -->
        <el-main>
          <div
            style="box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); border-radius: 8px; padding: 20px; background-color: #f5f7fa; margin-bottom: 20px;">
            是一段小有遗憾的快乐时光。
          </div>

          <div style="display: flex; flex-wrap: wrap; justify-content: space-between;">
            <el-card
              style="width: calc(50% - 10px); margin-bottom: 20px; border: none; box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); border-radius: 8px;">
              <div slot="header" class="clearfix">
                <span style="font-weight: bold; font-size: 16px;">看你挺会走路的，要不要一起散个步</span>
              </div>
              <div style="font-size: 14px; color: #606266;">
                我知道你玩我，但是这个无所谓，我也只是本能的对你好一些，我的日常无趣，性格又寡淡，也没有获得什么成就，很谢谢你陪我。
                <div style="margin-top: 20px;">
                  <div style="margin-bottom: 10px;"><strong>主题色</strong></div>
                  <el-button type="primary" size="small">1</el-button>
                  <el-button type="success" size="small">2</el-button>
                  <el-button type="warning" size="small">3</el-button>
                  <el-button type="danger" size="small">4</el-button>
                  <el-button type="info" size="small">5</el-button>
                </div>
              </div>
            </el-card>

            <el-card
              style="width: calc(50% - 10px); margin-bottom: 20px; border: none; box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); border-radius: 8px;">
              <div slot="header" class="clearfix">
                <span style="font-weight: bold; font-size: 16px;">看你挺会走路的，要不要一起散个步</span>
              </div>
              <div style="font-size: 14px; color: #606266;">
                我知道你玩我，但是这个无所谓，我也只是本能的对你好一些，我的日常无趣，性格又寡淡，也没有获得什么成就，很谢谢你陪我。
                <div style="margin-top: 20px;">
                  <div style="margin-bottom: 10px;"><strong>主题色</strong></div>
                  <el-button type="primary" size="small">1</el-button>
                  <el-button type="success" size="small">2</el-button>
                  <el-button type="warning" size="small">3</el-button>
                  <el-button type="danger" size="small">4</el-button>
                  <el-button type="info" size="small">5</el-button>
                </div>
              </div>
            </el-card>
          </div>
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
      asideWidth: '200px',
      collapseIcon: 'el-icon-s-fold'
    }
  },
  methods: {
    handleFull() {
      if (!document.fullscreenElement) {
        // 如果当前不是全屏状态，则请求全屏
        document.documentElement.requestFullscreen()
          .catch(err => {
            alert(`Error attempting to enable full-screen mode: ${err.message} (${err.name})`);
          });
      } else {
        // 如果当前是全屏状态，则退出全屏
        if (document.exitFullscreen) {
          document.exitFullscreen();
        }
      }
    },
    handleCollapse() {
      this.isCollapse = !this.isCollapse
      this.asideWidth = this.isCollapse ? '64px' : '200px'
      this.collapseIcon = this.isCollapse ? 'el-icon-s-unfold' : 'el-icon-s-fold'
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

.el-aside {
  transition: width .15s;
  border-radius: 10px !important;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.5) !important;
}

.el-menu {
  border-radius: 10px !important;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.5) !important;
}

.el-header {
  box-shadow: 2px 0 6px rgba(0, 21, 41, .35);
  display: flex;
  align-items: center;
}
</style>