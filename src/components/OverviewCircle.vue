<template>
  <div class="h-100">
    <div
      :class="[
        'circle p-4 m-2 text-white h-100',
        thirtyDayTotal <= 0 ? 'bg-danger' : 'bg-success'
      ]">
      <div class="circle-inner h-100">
        <div class="mx-auto my-auto">
          <h3>{{total.toLocaleString()}}</h3>
          <small class="smaller">
            <arrow-down-icon
              v-if="thirtyDayTotal <= 0"
            />
            <arrow-up-icon v-else />
            {{Math.abs(thirtyDayTotal)}} <i>last 30 days</i>
          </small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ArrowDownIcon from 'vue-material-design-icons/ArrowDown.vue'
import ArrowUpIcon from 'vue-material-design-icons/ArrowUp.vue'

export default {
  name: 'overview-circle',
  props: [
    'thirtyDayTotal',
    'total',
    'title'
  ],

  components: {
    ArrowDownIcon,
    ArrowUpIcon
  }
}
</script>

<style lang="scss" scoped>
.circle {
  border-radius: 50%;
  border: 3px solid white;

  -webkit-box-shadow: 0px 0px 5px 0px grey;
  -moz-box-shadow: 0px 0px 5px 0px grey;
  box-shadow: 0px 0px 5px 0px grey;

  .smaller {
    font-size: 50%;
  }
  // .circle-inner {
  //   box-shadow: 0 4px 2px -2px gray;
  // }
}
</style>
