<template>
  <div id="app">
    <input v-on:keyup="search" v-model="gamename" placeholder="modifiez-moi">
    <ul>
      <li v-for="game in gamelist" :key="game.id">
         <nuxt-link :to="{name: 'game', params: { appId:game.appid, search:gamename  } }">{{game.name}} - {{game.appid}}</nuxt-link>
       </li>
    </ul>
  </div>
</template>

<script>
      import json from '../data.json'
      export default{
          data(){
              return{
                  games: json.response.apps,
                  gamelist: [],
                  gamename: this.$route.params.search
              }
          },
          methods: {
            search () {
              console.log('début')
              this.gamelist = []
              let result = null
              result = this.games.filter(game => game.name.includes(this.gamename));
              if (result.length >= 1) {
                result.forEach(game => {
                  this.gamelist.push(game)
                });
              } else {
                  this.gamelist = []
              }

            },
            afterMounted() {
              search()
            },
          },
      }
</script>