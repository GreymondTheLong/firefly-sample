<template>
  <div class="h-100">
    <div
      :class="[
        'circle p-4 m-2 text-white h-100 shadow d-flex justify-content-between align-items-center',
        thirtyDayTotal <= 0 ? 'bg-danger' : 'bg-success'
      ]">
      <div class="circle-inner">
        <div class="mx-auto my-auto">
          <h3>{{total.toLocaleString()}}</h3>
          <small class="">
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
  min-width: 10rem;
  max-width: 10rem;
  min-height: 10rem;
  max-height: 10rem;

  .smaller {
    font-size: 60%;
  }
  // .circle-inner {
  //   box-shadow: 0 4px 2px -2px gray;
  // }
}
</style>
