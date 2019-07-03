<template>
  <div id="app" class="container-fluid h-100">
    <b-row class="h-100">
      <div id="nav" class="col-xs-12 col-sm-3 col-lg-2 p-0">
        <b-navbar toggleable="sm" class="h-100 p-0">
          <b-navbar-toggle target="nav-collapse">
            <menu-icon />
          </b-navbar-toggle>
          <b-collapse id="nav-collapse" is-nav class="h-100">
            <div class="d-flex flex-column justify-content-between h-100 w-100">
              <b-nav vertical>
                <b-navbar-brand href="#" class="mb-3">
                  <div class="d-flex justify-content-start">
                    <div class="w-25">
                      <img alt="Data Dashboard Logo" src="@/assets/ff_logo.png" class="img-fluid">
                    </div>
                    <div class="my-auto ml-2">
                      DataDashboard
                    </div>
                </div>
                </b-navbar-brand>
                <b-nav-item active>Overview</b-nav-item>
                <b-nav-item>Animals</b-nav-item>
                <b-nav-item>Food</b-nav-item>
                <b-nav-item>Music</b-nav-item>
              </b-nav>

              <div class="">
                <hr />
                <b-nav vertical>
                  <b-nav-item>Settings</b-nav-item>
                  <b-nav-item>Logout</b-nav-item>
                  <small class="text-center text-white">
                    &copy; FireFly 2019
                  </small>
                </b-nav>
              </div>
            </div>
          </b-collapse>
        </b-navbar>
      </div>
      <div class="col-sm-9 col-lg-10 px-0">
        <agreement-notification />
        <transition name="fade">
          <router-view class="pl-4"/>
        </transition>
      </div>
    </b-row>
  </div>
</template>

<script>
import MenuIcon from 'vue-material-design-icons/Menu.vue'
const AgreementNotification = () => import('./components/AgreementNotification.vue')

export default {
  components: {
    AgreementNotification,
    MenuIcon
  }
}
</script>

<style lang="scss">
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
#nav {
  background-color: rgb(6, 54, 71);
  a {
    font-weight: bold;
    color: #ffffff;
    &.active {
      color: #ffffff;
      background-color: rgb(31, 74, 89);
      border-left: 3px solid #ffffff;
      border-top: 1px solid #ffffff;
    }
  }
  li {
    text-align: left;
  }
  hr {
    border-color: var(--grey);
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
