.<template>
  <div class="container">      
              <ul v-if="inputHeader.length > 0" class="list-inline row row-cols-6 gap-3 justify-content-center">
                  <Card 
                    v-for="(film,index) in inputHeader" 
                    :key="index"
                    :title="film.title"
                    :original="film.original_title"
                    :language="film.original_language"
                    :vote="film.vote_average"
                  />
              </ul>
              <div class="row justify-content-center" v-else>
                  <div class="col-2">
                       Ricerca non correlata...
                  </div>                
              </div>
  </div>
</template>

<script>
import Card from './Card.vue'

export default {
    name:"Main",

    components:{
        Card,
    },

    props: ["inputHeader"],

}
</script>

<style lang="scss">
ul {
    list-style: none;
}
</style>