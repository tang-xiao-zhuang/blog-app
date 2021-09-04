<template>
  <el-aside width="200px">
    <div style="margin-top: 500px">
      <el-row class="tac">
        <el-col :span="24">
          <el-menu default-active="1" class="el-menu-vertical-demo" @select="menuSelect">
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
            <el-menu-item index="/register">
              <i class="el-icon-menu"></i>
              <span slot="title">注册</span>
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
  methods: {
    menuSelect(index) {
      this.$router.push({path: index})
    },
    logout() {
      let that = this
      this.$store.dispatch('logout').then(() => {
        this.$router.push({path: '/'})
      }).catch((error) => {
        if (error !== 'error') {
          that.$message({message: error, type: 'error', showClose: true});
        }
      })
    }

  }
}
</script>

<style scoped>

</style>
