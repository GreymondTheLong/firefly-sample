<template>
  <div id="agreement" class="w-100 p-4 mb-4">
    <h2>Welcome!</h2>
    <p>
      Before you get carried away, do you agree to us collection anonimized statistics about your usage of our app?
    </p>
    <div>
      <b-btn variant="outline-info" class="mr-1">
        <close-icon /> Disagree
      </b-btn>

      <b-btn variant="info" class="ml-1">
        <check-icon/> I agree
      </b-btn>
    </div>
  </div>
</template>

<script>
import CloseIcon from 'vue-material-design-icons/Close.vue'
import CheckIcon from 'vue-material-design-icons/Check.vue'

export default {
  name: 'agreement-notification',
  components: {
    CloseIcon,
    CheckIcon
  }
}
</script>

<style lang="scss" scoped>
#agreement {
  background-color: rgb(214, 235, 243);

  -webkit-box-shadow: 0px 5px 10px -2px gray;
  -moz-box-shadow: 0px 5px 10px -2px gray;
  box-shadow: 0px 5px 10px -2px gray;

  // .btn-outline-info {
  //   background-color: #ffffff;
  //   &:hover{
  //     color: theme-color("info")
  //   }
  // }
}
</style>
