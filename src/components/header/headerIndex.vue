<template>
  <el-container>
    <el-header>
      <el-menu :default-active="activeIndex" class="headerMenu" mode="horizontal">
        <el-menu-item class="logoItem">
          <el-image
            class="logo"
            :src="require('@/assets/logo.png')"
            fit="contain">
          </el-image>
        </el-menu-item>
        <el-menu-item index="1" v-model="activeIndex">首页</el-menu-item>
        <el-menu-item index="2" v-model="activeIndex">景点</el-menu-item>
        <el-menu-item index="3" v-model="activeIndex">旅游攻略</el-menu-item>
        <el-menu-item index="4" v-model="activeIndex">订酒店</el-menu-item>
        <el-menu-item index="5" v-model="activeIndex">视觉城市</el-menu-item>
        <div class="authContainer">
          <div v-if="!isLogin" class="loginContainer">
            <span @click="login" style="cursor: pointer">登录</span>
            <span class="split">|</span>
            <span @click="register" style="cursor: pointer">注册</span>
          </div>
          <div v-else class="avatarContainer">
            <el-avatar :size="36" :src="require('@/assets/avatar.jpg')" class="avatar" @click="logout"></el-avatar>
          </div>
        </div>
      </el-menu>
    </el-header>
  </el-container>

</template>

<script>
export default {
  data() {
    return {
      activeIndex: '1',
      isLogin: false,
    };
  },
  methods: {
    login() {
      this.isLogin = true;
    },
    logout() {
      this.isLogin = false;
    }

  }
}
</script>

<style scoped>
.el-container {

}
.el-header {
  padding: 0 0;
}
.headerMenu {
  width: 100%;
  display: flex;
  justify-content: center;
  position: relative;
  background-color: transparent;  /* 初始背景透明 */
  transition: background-color 0.3s;  /* 添加过渡效果 */
}
.headerMenu:hover {
  background-color: #FFFFFF;  /* 鼠标移动时背景变为白色 */
}
.el-menu-item {
  font-size: 18px;
}
.logoItem {
  pointer-events: none;
  user-select: none;
}
.logo {
  width: 50px;
  height: 50px;
}
.authContainer {
  position: absolute;
  right: 400px;
  top: 25px;
}
.loginContainer {
  color: #2ec4b6;
}
.split {
  display: inline-block;
  margin: 0 10px;
  width: 1px;
  height: 14px;
  background-color: #c9c9c9;
  overflow: hidden;
  vertical-align: -2px;
}
.avatar {
  cursor: pointer;
}
</style>