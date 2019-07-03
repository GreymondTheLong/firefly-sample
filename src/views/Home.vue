<template>
  <div class="home">
    <div class="mb-4">
      <h3 class="text-left ml-2">Overview</h3>
      <div class="d-flex flex-column flex-sm-row justify-content-between w-100">
        <template v-for="(overview, index) in overviewData">
          <overview-circle
            :key="index"
            :total="overview.total"
            :title="overview.title"
            :thirtyDayTotal="overview.lastThirtyDaysValue"
          />
        </template>
      </div>
    </div>
    <h3 class="text-left ml-2">Top Music</h3>
    <b-tabs>
      <b-tab title="Artists">
        <b-table :items="topMusic" :fields="topMusicFields">
          <template slot="HEAD_index">
            #
          </template>
        </b-table>
      </b-tab>
      <b-tab title="Songs" disabled>
      </b-tab>

      <b-tab disabled>
        <template slot="title">
          Moods
          <b-badge :variant="warning">
            21
          </b-badge>
        </template>
      </b-tab>
  </div>
</template>

<script>
// @ is an alias to /src
import OverviewCircle from '@/components/OverviewCircle.vue'

export default {
  name: 'home',
  components: {
    OverviewCircle
  },

  data () {
    return {
      overviewData: [
        {
          title: 'Cat videos watched',
          total: 198,
          lastThirtyDaysValue: -84
        }, {
          title: 'Slices of pizza in the fridge',
          total: 5,
          lastThirtyDaysValue: 2
        }, {
          title: 'Favorite songs beginning with the letter \'A\'',
          total: 1324,
          lastThirtyDaysValue: 23
        }
      ],
      topMusicFields: [
        'index',
        'artist',
        'plays',
        'songs',
        { key: 'actions', label: '' } // actions
      ],
      topMusic: [{
        artist: 'The Wiggles',
        plays: 86340,
        songs: 189
      }, {
        artist: 'Dolly Parton',
        plays: 86333, 
        songs: 244 
      }, {
        artist: 'Wellington International Ukelele Orchestra', 
        plays: 85023, 
        songs: 12
      }]
    }
  }
}
</script>
