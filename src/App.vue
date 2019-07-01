<template>
  <div id="app" class="container-fluid">
    <b-row>
    <div class="col-xs-12 col-sm-2">
    <b-nav vertical>
      <b-nav-item active>Overview</b-nav-item>
      <b-nav-item>Animals</b-nav-item>
      <b-nav-item>Food</b-nav-item>
      <b-nav-item>Music</b-nav-item>
    </b-nav>
    </div>
    <div class="col-sm-10">
      <!-- Import agreement component -->
      <agreement-notification />
      <transition name="fade">
        <router-view/>
      </transition>
    </div>
    </b-row>
  </div>
</template>

<script>
const AgreementNotification = () => import('./components/AgreementNotification.vue')

export default {
  components: {
    AgreementNotification
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
