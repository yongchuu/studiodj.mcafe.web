<template>
  <v-container fluid grid-list-md>
    <v-layout row wrap>
      <v-flex d-flex
        v-for="(card, idx) in cards"
        v-bind="{ [`xs${flex}`]: true }"
        :key="idx"
      >
        <v-card>
          <v-card-media
            class="white--text"
            height="200px"
            :src="card.src"
            v-if="card.src != ''"
          >
            <v-layout
              column class="media"
              @click.stop="toRoute('vuejs_view_article',{id: card.id})"
              style="cursor: pointer"
            >
              <v-card-title>
                <v-spacer></v-spacer>
                <v-btn dark icon>
                  <v-icon>thumb_up</v-icon>
                </v-btn>
              </v-card-title>
              <v-spacer></v-spacer>
              <v-card-title class="white--text pt-5">
                <div class="body-2 pl-5 pt-5">{{card.meta}}</div>
              </v-card-title>
            </v-layout>
          </v-card-media>
          <v-card-title>
            <div>
              <v-flex class="title"
                @click.stop="toRoute('vuejs_view_article',{id: card.id})"
                style="cursor: pointer"
              >{{card.title}}</v-flex>
              <v-flex class="body-1">
                <span v-if="card.subtitle.length > 140" class="grey--text">
                  {{card.subtitle.substring(0, 140)}}... &nbsp;&nbsp;
                  <a href="#">read more</a>
                </span>
                <span v-else class="grey--text">
                  {{card.subtitle}} &nbsp;&nbsp;
                </span>
              </v-flex>
            </div>
              <v-layout row wrap>
                <v-flex
                  v-for="(topic, index) in card.topics"
                  :key="index"
                >
                  <a href="">{{topic}}</a>
                </v-flex>
              </v-layout>
          </v-card-title>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: 'GridCards',
  created () {
  },
  data: () => ({
    cards: [
      {
        meta: 'Back Eunbi',
        title: 'Back Eunbi',
        subtitle: '안녕하세요. 안녕하세요. 안녕하세요. 안녕하세요. 안녕하세요. 안녕하세요.',
        src: 'https://pds.joins.com/news/component/htmlphoto_mmdata/201910/26/ce877ed2-0800-457f-b9a6-a86044718d40.jpg',
        created: '15 min',
        topics: ['상봉동', '은비맘', '배고파', '배봉초'],
        id: 1
      },
      {
        meta: 'Ju Dongjoon',
        title: 'Ju Dongjoon',
        subtitle: '반갑습니다. 반갑습니다. 반갑습니다. 반갑습니다. 반갑습니다. 반갑습니다.',
        src: 'https://pds.joins.com/news/component/htmlphoto_mmdata/201910/26/c4e0e76e-e838-4693-9eca-e18ec9cc4aee.jpg',
        created: '15 min',
        topics: ['광교', '동준맘', '삼성SDS'],
        id: 2
      }
    ]
  }),
  computed: {
    flex () {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs': return 12
        case 'sm': return 6
        case 'md': return 4
        case 'lg': return 3
        case 'xl': return 2
      }
    }
  },
  methods: {
    toRoute (rname, rparams = {}, query = {}) {
      this.dialog = true
      this.$router.push({name: rname, params: rparams, query: query})
    }
  }
}
</script>