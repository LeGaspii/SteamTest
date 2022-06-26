<template>
  <div id="app">
    <p>coucou</p>
  </div>
</template>

<script>
      export default{
          data(){
              return{
                gamedata: []
              }
          },
        mounted() {
          axios
            .get(axios.baseURL+'/appdetails?appids='+appId)
            .then(response => (this.gamedata = response))
        },  
      }
</script>