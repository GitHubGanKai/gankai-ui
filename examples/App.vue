<template>
  <div>
    <mainHeader>
    </mainHeader>
    <div class="app-body" v-if="!isIndex">
      <sideNav class="nav"></sideNav>
      <router-view class="view"></router-view>
    </div>
    <router-view class="page" v-else></router-view>
  </div>
</template>

<script>
import mainHeader from "./components/header.vue";
import mainFooter from "./components/footer.vue";
import sideNav from "./components/side-nav.vue";

export default {
  data() {
    return {
      init: false,
      isIndex: false
    };
  },
  watch: {
    $route() {
      this.isIndex = this.$route.name === "index";
    }
  },
  mounted() {
    //  这里模拟数据请求
    setTimeout(() => {
      this.init = true;
    }, 250);
  },
  components: {
    mainHeader,
    sideNav,
    mainFooter
  }
};
</script>

<style lang="scss" scoped>
.app-body {
  margin: 20px 10%;
  margin-top: 80px;
  display: flex;
  flex-direction: row;
  .nav {
    flex: 1;
  }
  .view {
    flex: 5;
    padding: 32px 48px 48px;
    box-sizing: border-box;
  }
}

.app-body:after {
  content: "";
  clear: both;
  display: block;
}
</style>