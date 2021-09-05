<template>
  <el-aside width="10%" style="background-color: #00d1b2">
<!--    &lt;!&ndash;    头像&ndash;&gt;-->
<!--    <div class="block">-->
<!--      <div>-->
<!--        <el-avatar size="100" :src="circleUrl"></el-avatar>-->
<!--      </div>-->
<!--      <span>-->
<!--        <el-button>登录</el-button>-->
<!--      </span>-->
<!--    </div>-->
    <!--导航拦-->
    <div style="margin-top: 500px">
      <el-row class="tac">
        <el-col :span="24">
          <el-menu default-active="1" class="el-menu-vertical-demo" @select="menuSelect"
                   style="background-color: #00d1b2">
            <el-submenu index="/">
              <template slot="title">
                <i class="el-icon-location"></i>
              </template>
              <el-menu-item-group>
                <el-menu-item index="/">首页</el-menu-item>
                <el-menu-item index="/category/all">文章分类</el-menu-item>
                <el-menu-item index="/tag/all">标签</el-menu-item>
                <el-menu-item index="/archives">归档</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
            <el-menu-item index="l" disabled>
              <i class="el-icon-menu"></i>
              <span slot="title">音乐</span>
            </el-menu-item>
            <el-menu-item index="/login">
              <i class="el-icon-menu"></i>
              <span slot="title">登录</span>
            </el-menu-item>
          </el-menu>
        </el-col>
      </el-row>
    </div>
  </el-aside>
</template>

<script>
export default {
  name: "publicAside",
  data() {
    return {
      circleUrl: "https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png",
    }
  },
  methods: {
    menuSelect(index) {
      this.$router.push({path: index})
    },
  }
}
</script>

<style scoped>
.block{
  margin-top: 20px;
  margin-left: 20px;
}
</style>
