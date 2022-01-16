<template>
    <div>
        <v-container>
            <v-flex xs12 pb-5>
            <h2>Latest News</h2>
            </v-flex>

    <v-flex>
    <v-flex xs12 pb-3 sm6 offset-sm3 v-for="(article, index) in articles" :key=index>        
    <v-card
    class="mx-auto"
    max-width="500"
  >
    <img
      :src="article.urlToImage"
      width="100%"
      height="250px"
    >

    <v-card-title>
      {{article.title}}
    </v-card-title>
    <v-card-text>{{article.content}}</v-card-text>
    <v-card-actions>
      <v-spacer></v-spacer>
      <v-btn flat :href="article.url" target="_blank">Open</v-btn>
    </v-card-actions>
     
  
        </v-card>
        </v-flex>
        </v-flex>
        </v-container>
    </div>
</template>

<script>
export default {
    async asyncData(app){
        const {articles} = await app.$axios.$get('https://newsapi.org/v2/everything?q=At&apiKey=9254d795e0784ea9885928957d071cb9');
        return {articles};
    }
    
}
</script>
