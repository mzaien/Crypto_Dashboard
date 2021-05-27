
<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <div class="text-center">
          <h1 v-text="route +' coin'"></h1>
      </div>
      <v-card>
        <v-card-title class="headline">
         <p v-if="$fetchState.pending">Fetching health...</p>
          <p v-else-if="$fetchState.error">An error occurred :(</p>
         <div v-else >
          <h3>{{route}} health</h3>
          <div v-for="(health,id) in healths" :key="id">
          <p>
                {{Object.keys(health)[2]}}: {{Object.values(health)[2]}}
          </p>
          <p>
                {{Object.keys(health)[6]}}: {{Object.values(health)[6]}}
          </p>
          </div>
         <button @click="$fetch">Refresh</button>
  </div>
        </v-card-title>
      </v-card>
    </v-col>
  </v-row>
</template>

<script >

export default {
    head:{
    title:"coin page"
    },
    mounted (){
    //  console.log("health"+ this.health)
    }
    ,
      data () {
    return {
      pageNotFound: '404 Not Found',
      route:  this.$route.params.id,
      healths:[]
    }
  },
     async fetch() {
      this.healths = await fetch(
        `https://www.alphavantage.co/query?function=CRYPTO_RATING&symbol=${this.route}&apikey=${process.env.API_KEY}`
      ).then(res => res.json())
    }
}
</script>
