<template>
  <div class="top-bar-box">
    <div class="top-bar-logo">
      <slot name="logo"></slot>
    </div>
    <div class="top-bar-menu">
      <el-menu :show-timeout="200" :default-active="$route.path" mode="horizontal" menu-trigger="hover" :background-color="bgColor" text-color="#fff" active-text-color="#409EFF">
        <topbar-item v-for="route in permission_routers" :key="`${route.path}_${Math.random() * 10000}`" :item="route" :base-path="route.path" style="max-width:120px;float:left;display:block;"/>
      </el-menu>
    </div>
    <div class="top-bar-info">
      <slot name="info"></slot>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import TopbarItem from './TopbarItem'
export default {
  name: 'TopBar',
  components: { TopbarItem },
  props: {
    bgColor: {
      type: String,
      default: '#4caf50'
    }
  },
  computed: {
    ...mapGetters([
      'permission_routers',
      'sidebar'
    ])
  }
}
</script>
<style>
.el-menu-item.submenu-title-noDropdown{
  min-width: 100px;
}
.nest-menu{
  min-width: 200px;
}
</style>