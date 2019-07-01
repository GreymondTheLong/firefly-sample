<template>
  <div class="w-100 p-4">
    <h2>Welcome!</h2>
    <p>
      Before you get carried away, do you agree to us collection anonimized statistics about your usage of our app?
    </p>
    <div>
      <b-btn>
        <close-icon /> Disagree
      </b-btn>
      <b-btn>
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

<style>

</style>
