<template>
  <v-card>
    <v-container
      fluid
      grid-list-lg
    >
      <v-layout row wrap>
        
        <v-flex xs12>
          <v-card color="white" class="black--text">
            <v-card-title primary-title>
              <div>
                <v-icon size="17px">mdi-information-outline</v-icon><span> 공지</span>
              </div>
            </v-card-title>
            <v-card-actions>
              <ul>
                <li
                  class="article lighten--text"
                  style="list-style-type: none;"
                  v-for="(article, idx) in notices" :key="idx">
                  <div v-if="article.link.indexOf('http') >= 0" class="title-font" @click="toExtRoute(article.link)"> [{{article.boardNm}}] {{article.title}} </div>
                  <div v-else class="title-font" @click="toRoute('vuejs_home')"> [{{article.boardNm}}] {{article.title}} </div>
                </li>
              </ul>
            </v-card-actions>
          </v-card>
        </v-flex>
        
        <v-flex xs12>
          <v-card color="white" class="black--text">
            <v-card-title primary-title>
              <div>
                <v-icon size="17px">mdi-book-open-outline</v-icon><span> 내가 쓴글</span>
              </div>
            </v-card-title>
            <v-card-actions>
              <ul>
                <li
                  class="article lighten--text"
                  style="list-style-type: none;"
                  v-for="(article, idx) in mynotes" :key="idx">
                  <div v-if="article.link.indexOf('http') >= 0" class="title-font" @click="toExtRoute(article.link)"> [{{article.boardNm}}] {{article.title}} </div>
                  <div v-else class="title-font" @click="toRoute('vuejs_home')"> [{{article.boardNm}}] {{article.title}} </div>
                </li>
              </ul>
            </v-card-actions>
          </v-card>
        </v-flex>
 
        <v-flex xs12 style="padding-bottom:24px;">
          <v-card color="white" class="black--text">
            <v-card-title primary-title>
              <div>
                <v-icon size="17px">mdi-shape-outline</v-icon><span> 마이 카테고리</span>
              </div>
            </v-card-title>
            <v-card-actions>
              <ul>
                <li
                  class="article lighten--text"
                  style="list-style-type: none;"
                  v-for="(article, idx) in catagorys" :key="idx">
                  <div v-if="article.link.indexOf('http') >= 0" class="title-font" @click="toExtRoute(article.link)"> [{{article.boardNm}}] {{article.title}} </div>
                  <div v-else class="title-font" @click="toRoute('vuejs_home')"> [{{article.boardNm}}] {{article.title}} </div>
                </li>
              </ul>
            </v-card-actions>
          </v-card>
        </v-flex>

      </v-layout>
    </v-container>
  </v-card>
</template>
<script>

export default {
  name: 'Home',
  created () {
  },
  data: () => ({
    show: false,
    isList: false,
    notices: [
      {title: '최신 버전 업데이트 안내 v1.0.13', boardNm: '공지', link: 'vuejs_home'},
      {title: '가족 휴가 사진 콘테스트', boardNm: '이벤트', link: 'vuejs_home'},
      {title: '최신 버전 업데이트 안내 v1.0.12', boardNm: '공지', link: 'vuejs_home'},
      {title: '최신 버전 업데이트 안내 v1.0.11', boardNm: '공지', link: 'vuejs_home'},
      {title: '최신 버전 업데이트 안내 v1.0.10', boardNm: '공지', link: 'vuejs_home'},
      {title: '최신 버전 업데이트 안내 v1.0.9', boardNm: '공지', link: 'vuejs_home'}
      // {title: 'Go + Gin + ElasticSearch - Modular rest engine', boardNm: 'June 18\'', link: 'https://github.com/nareshganesan/services/tree/dev'}
    ],
    mynotes: [
      {title: '상봉동 우리동네 맛집 V02', boardNm: '쫑알쫑알', link: 'vuejs_home', view: '1,004', comments: '10'},
      {title: '또봐도 배봉초 백은비 선생님 너무 예뻐요', boardNm: '초등맘', link: 'vuejs_home', view: '1,211,004', comments: '5,030'},
      {title: '집에서 맛있는 김치볶음밥 만들기', boardNm: '쫑알쫑알', link: 'vuejs_home', view: '1,004', comments: '10'},
      {title: '공덕 살만한곳 추천 부탁드립니다.', boardNm: '초등맘', link: 'vuejs_home', view: '1,211,004', comments: '5,030'},
      {title: '아무리봐도 배봉초 백은비 선생님 너무 예뻐요', boardNm: '초등맘', link: 'vuejs_home', view: '1,211,004', comments: '5,030'},
      {title: '상봉동 우리동네 맛집 V01', boardNm: '쫑알쫑알', link: 'vuejs_home', view: '1,004', comments: '10'},
      {title: '배봉초 백은비 선생님 너무 예뻐요', boardNm: '초등맘', link: 'vuejs_home', view: '1,211,004', comments: '5,030'}
      // {title: 'Go + Gin + ElasticSearch - Modular rest engine', created: 'June 18\'', link: 'https://github.com/nareshganesan/services/tree/dev'}
    ],
    catagorys: [
      {title: '3학년 영어학원 추천해주세요', boardNm: '초등맘', link: 'vuejs_home', view: '1,004', comments: '10'},
      {title: '우리 애가 코로나 걸린거같아요.', boardNm: '초등맘', link: 'vuejs_home', view: '210,004', comments: '2,059'},
      {title: '주식투자 누구나 할 수있다.', boardNm: '재테크', link: 'vuejs_home', view: '1,004', comments: '10'},
      {title: '3학년 영어학원 나 할 수있다.', boardNm: '재테크', link: 'vuejs_home', view: '1,004', comments: '10'}
      // {title: 'Go + Gin + ElasticSearch - Modular rest engine', created: 'June 18\'', link: 'https://github.com/nareshganesan/services/tree/dev'}
    ]
  }),
  methods: {
    toRoute (rname, rparams = {}, query = {}) {
      this.dialog = true
      this.$router.push({name: rname, params: rparams, query: query})
    },
    toExtRoute (rname) {
      window.location = rname
      return false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import url('https://fonts.googleapis.com/css?family=Archivo')

.article {
  /*font-family: 'Archivo', sans-serif, Helvetica;*/
  list-style-type: none;
  font-size: 18px !important;
  font-weight: 400;
  cursor: pointer;
}

.title-font {
  /*Google fonts: Archivo*/
  font-family: 'Archivo', sans-serif, Helvetica;
  font-size: 16px !important;
  font-weight: 400;
  cursor: pointer;
  color: #616161;
  line-height: 1.8;
}

.content-font {
  /*Google fonts: Work Sans*/
}

.note-font {
  /*Google fonts: playfair display*/
}

</style>
`