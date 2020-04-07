<template>
  <v-footer
    v-model="bottomNav"
    v-bind="localAttrs"
    
    height="auto"
    width="100%"
    color="grey lighten-5"
  >
    <v-layout
      justify-center
       row
       wrap>
      <v-btn 
        v-for="menu in menus" 
        :key="menu.name"
        color="grey"
        flat
        round
        padless="true"
        class="mx-4"
        small
        icon>
        <v-icon size="27px">{{ menu.icon }}</v-icon>
        <!-- <span v-html='menu.name'></span> -->
      </v-btn>
    </v-layout>
  </v-footer>
</template>

<script>
  export default {
    name: 'BottomNav',
    data () {
      return {
        menus: [
          {
            name: 'Home',
            icon: 'mdi-home'
          },
          {
            name: '게시판',
            icon: 'mdi-clipboard-text-outline'
          },
          {
            name: '육아교육',
            icon: 'mdi-school'
          },
          {
            name: '채팅방',
            icon: 'mdi-chat-processing'
          },
          {
            name: 'My page',
            icon: 'mdi-account'
          }
        ],
        bottomNav: 3
      }
    },
    computed: {
      localAttrs () {
        const attrs = {}
        attrs['fixed'] = true
        return attrs
      },
      color () {
        switch (this.bottomNav) {
          case 0: return 'blue-grey'
          case 1: return 'teal'
          case 2: return 'brown'
          case 3: return 'indigo'
        }
      }
    }
  }
</script>