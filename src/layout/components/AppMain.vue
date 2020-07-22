<template>
  <section class="app-main">
    <div class="main">
      <breadcrumb class="breadcrumb-container" />
      <transition name="fade-transform" mode="out-in">
        <div class="page">
          <router-view :key="key" />
        </div>
      </transition>
    </div>
  </section>
</template>

<script>
import Breadcrumb from '@/components/Breadcrumb'

export default {
  name: 'AppMain',
  components: {
    Breadcrumb,
  },
  computed: {
    key() {
      return this.$route.path
    }
  }
}
</script>

<style scoped>
.app-main {
  /*50 = navbar  */
  min-height: calc(100vh - 50px);
  height: calc(100vh - 50px);
  width: calc(100% - 180px);
  position: relative;
  overflow: hidden;
  margin-left: 180px;
  margin-top: 50px;
  .breadcrumb-container {
    float: left;
  }
  
  
}
.main {
    margin: 15px;
    height: calc(100% - 80px);
    box-shadow: 1px 1px 4px rgba(0, 21, 41, 0.08);
  }
.page {
    overflow-y: auto;
    height: 100%;
  }
.fixed-header+.app-main {
  padding-top: 50px;
}
</style>

<style lang="scss">
// fix css style bug in open el-dialog
.el-popup-parent--hidden {
  .fixed-header {
    padding-right: 15px;
  }
}
</style>
