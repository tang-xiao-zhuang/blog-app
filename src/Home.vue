<template>
  <div id="home">
    <el-container>
<!--      <base-header :activeIndex="activeIndex"></base-header>-->
      <el-aside width="10%" style="background-color: #FFFFFF">
        <public_aside/>
      </el-aside>

      <el-main>
        <router-view/>
      </el-main>
    </el-container>

  </div>

</template>

<script>
import BaseFooter from '@/components/BaseFooter'
import BaseHeader from '@/views/BaseHeader'
import PublicAside from '@/components/aside/publicAside'

export default {
  name: 'Home',
  data() {
    return {
      activeIndex: '/',
      footerShow: true
    }
  },
  components: {
    'base-header': BaseHeader,
    'base-footer': BaseFooter,
    "public_aside": PublicAside
  },
}
</script>

<style>

.me-container {
}
</style>
