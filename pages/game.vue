<template>
  <div class="container col-12">
    <nuxt-link class="btn btn-succes" :to="{name: 'index', params: { search:$route.params.search } }">Go back</nuxt-link>
    <div>
      <h1>{{gameData[$route.params.appId].data.name}}</h1>
      <img :src="gameData[$route.params.appId].data.header_image" alt="Header">
      <p>{{$route.params.appId}}</p>
      <p>prix: {{gameData[$route.params.appId].data.price_overview.final}}</p>
      <p>{{gameData[$route.params.appId].data.release_date.date}}</p>
      <p>{{gameData[$route.params.appId].data.detailed_description}}</p>
    </div>

  </div>
</template>


<script>

  export default {
    data() {
      return {
        id: 0,
        gameData: []

      }
    },
    async asyncData({ params, $axios }) {
      console.log('search for :', params.appId)
      const gameData = await $axios.$get('https://store.steampowered.com/api/appdetails?appids='+params.appId)
      return { gameData }
    },
  }
  </script>
  <style>
  </style>