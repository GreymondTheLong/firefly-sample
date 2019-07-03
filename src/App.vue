h<template>
  <div id="app" class="container-fluid h-100">
    <b-row class="h-100 pb-3">
      <div id="nav" class="col-xs-12 col-sm-3 col-lg-2 p-0">
        <div class="d-flex flex-column flex-fill flex-grow-1 h-100">
          <b-navbar toggleable="sm" class="p-0 h-100">
            <b-navbar-toggle target="nav-collapse">
              <menu-icon class="text-white" />
            </b-navbar-toggle>
            <div class="py-1">
              <!-- FIXME: sloppy inline style. needs moving to a class -->
              <img alt="Data Dashboard Logo" src="@/assets/ff_logo.png" class="img-fluid d-block d-sm-none float-right" style="max-height: 2rem;">
            </div>
            <b-collapse id="nav-collapse" is-nav class="h-100">
              <div class="d-flex flex-column justify-content-between flex-fill w-100">
                <b-nav vertical>
                  <b-navbar-brand
                    href="#"
                    class="mb-3 d-none d-sm-block"
                  >
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
                  <hr class="d-none d-sm-block" />
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
      </div>
      <div class="col-sm-9 col-lg-10 px-0 pb-3">
        <transition name="slide">
          <agreement-notification
            v-if="showingAgreement"
            @agree="showingAgreement = false"
            @disagree="showingAgreement = false"
          />
        </transition>
        <transition name="fade">
          <router-view class="px-4"/>
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
  },
  data () {
    return {
      showingAgreement: true
    }
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

.slide-enter-active {
   -moz-transition-duration: 0.3s;
   -webkit-transition-duration: 0.3s;
   -o-transition-duration: 0.3s;
   transition-duration: 0.3s;
   -moz-transition-timing-function: ease-in;
   -webkit-transition-timing-function: ease-in;
   -o-transition-timing-function: ease-in;
   transition-timing-function: ease-in;
}

.slide-leave-active {
   -moz-transition-duration: 0.3s;
   -webkit-transition-duration: 0.3s;
   -o-transition-duration: 0.3s;
   transition-duration: 0.3s;
   -moz-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   -webkit-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   -o-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
}

.slide-enter-to, .slide-leave {
   max-height: 100px;
   overflow: hidden;
}

.slide-enter, .slide-leave-to {
   overflow: hidden;
   max-height: 0;
}

@media (min-width: 768px) {
  #nav-collapse > div {
    height: 100%;
  }
}
</style>
