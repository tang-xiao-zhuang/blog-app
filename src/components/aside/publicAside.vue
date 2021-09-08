<template>

  <div>
    <!--logo-->
    <div align="center">
      <div style="margin-top: 25%">
        <img :src="logoImgUrl" width="160" height="80">
      </div>

      <br/>

      <!--头像-->
      <div style="width: 80px;height: 80px; border-radius:40px;overflow: hidden; margin-top: 20%" @click="profileClick">
        <img :src="circleUrl" alt="picture"  style="width: 80px;height: 80px;">
      </div>

    </div>


    <!--导航拦-->
    <div style="margin-top:50%">
      <el-row>
        <el-col :span="24">
          <el-menu default-active="1" class="el-menu-vertical-demo" @select="menuSelect">
            <el-menu-item index="/">
              <i class="el-icon-menu"></i>
              <span slot="title">首页</span>
            </el-menu-item>
            <el-submenu>
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>分类</span>
              </template>
              <el-menu-item-group>
                <el-menu-item index="/write">写文章</el-menu-item>
                <el-menu-item index="/category/all">文章分类</el-menu-item>
                <el-menu-item index="/tag/all">标签</el-menu-item>
                <el-menu-item index="/archives">归档</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
            <el-menu-item index="l" disabled>
              <i class="el-icon-menu"></i>
              <span slot="title">音乐</span>
            </el-menu-item>

            <el-submenu>
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>其他</span>
              </template>
              <el-menu-item-group>
                <el-menu-item index="l" disabled>
                  <i class="el-icon-menu"></i>
                  <span slot="title">关于我们</span>
                </el-menu-item>
                <el-menu-item index="l" disabled>
                  <i class="el-icon-menu"></i>
                  <span slot="title">联系我们</span>
                </el-menu-item>
              </el-menu-item-group>
            </el-submenu>
          </el-menu>
        </el-col>
      </el-row>
    </div>
  </div>


</template>

<script>
export default {
  name: "publicAside",
  data() {
    return {
      circleUrl: "http://qyyuq8wkj.hn-bkt.clouddn.com/1292e567-bd8d-4880-911d-f128f61686b0.png",
      logoImgUrl: "http://qyyuq8wkj.hn-bkt.clouddn.com/9e702c8a-f267-4994-9922-69f91560208e.png",
    }
  },
  methods: {
    menuSelect(index) {
      console.log(index)
      this.$router.push({path: index})
    },
    profileClick() {
      if (this.circleUrl ===  "http://qyyuq8wkj.hn-bkt.clouddn.com/1292e567-bd8d-4880-911d-f128f61686b0.png") {
        this.login()
      } else {
        this.logout()
      }
    },
    login() {
      this.$router.push({path: "/login"})
      this.circleUrl = "http://qyyuq8wkj.hn-bkt.clouddn.com/7cbc845a-7803-45a3-a9fe-97b7856d653c.png"
    },
    logout() {
      let that = this
      this.$store.dispatch('logout').then(() => {
        this.circleUrl =  "http://qyyuq8wkj.hn-bkt.clouddn.com/1292e567-bd8d-4880-911d-f128f61686b0.png"
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
.block {
  margin-top: 20px;
  margin-left: 20px;
}
</style>
