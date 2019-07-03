<template>
  <div class="pt-4">
    <div class="mb-4">
      <h3 class="text-left ml-2">Overview</h3>
      <div class="d-flex flex-column flex-sm-row justify-content-between align-items-center w-100">
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
    <b-card no-body="" class="shadow bg-white">
      <b-tabs card>
        <b-tab title="Artists">
          <b-table
            :items="topMusic"
            :fields="topMusicFields"
            stacked="sm"
          >
            <template slot="HEAD_rank">
              #
            </template>

            <template slot="actions" slot-scope="data">
              <b-btn variant="link">
                <trash-can-icon class="text-danger" @click="removeRecord(data.item.rank)" />
              </b-btn>
              <share-variant-icon class="text-info" />
            </template>
          </b-table>
        </b-tab>
        <b-tab title="Songs" disabled>
        </b-tab>

        <b-tab disabled>
          <template slot="title">
            Moods
            <b-badge variant="warning" class="text-white">
              21
            </b-badge>
          </template>
        </b-tab>
      </b-tabs>
      <template slot="footer">
        <b-row>
          <b-btn variant="info" class="ml-auto">
            View more music data <chevron-right-icon :size="32" />
          </b-btn>
        </b-row>
      </template>
    </b-card>
  </div>
</template>

<script>
// @ is an alias to /src
import OverviewCircle from '@/components/OverviewCircle.vue'
import ChevronRightIcon from 'vue-material-design-icons/ChevronRight.vue'
import TrashCanIcon from 'vue-material-design-icons/TrashCan.vue'
import ShareVariantIcon from 'vue-material-design-icons/ShareVariant.vue'

export default {
  name: 'home',
  components: {
    OverviewCircle,
    ChevronRightIcon,
    TrashCanIcon,
    ShareVariantIcon
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
        'rank',
        'artist',
        'plays',
        'songs',
        { key: 'actions', label: '' }
      ],
      topMusic: [{
        rank: 1,
        artist: 'The Wiggles',
        plays: 86340,
        songs: 189
      }, {
        rank: 2,
        artist: 'Dolly Parton',
        plays: 86333,
        songs: 244
      }, {
        rank: 3,
        artist: 'Wellington International Ukelele Orchestra',
        plays: 85023,
        songs: 12
      }]
    }
  },

  methods: {
    removeRecord (rank) {
      // TODO: use something other than rank
      this.topMusic = this.topMusic.filter(music => music.rank !== rank)
    }
  }
}
</script>
