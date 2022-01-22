.<template>
  <div class="container text-white"> 
      <div v-if="valueBooleanFilm" class="movie">
          <h1 class="text-center mt-5 mb-5">Movies</h1>
             <ul class="list-inline row row-cols-3 row-cols-md-4 row-cols-lg-5 gap-5 justify-content-center">
                <Card
                v-for="(film,index) in filmAndMovies.films" 
                :key="index+ '-' +film.id"
                :title="film.title"
                :original="film.original_title"
                :language="film.original_language"
                :vote="film.vote_average"
                :img="film.poster_path"
                :overview="film.overview"
                />
            </ul>
          </div>     
           
            <div class="row justify-content-center" v-else-if="valueBooleanFilm == false">
                <div class="col-2">
                    nessun film trovato...
                </div>                
            </div>
            
            <div v-if="valueBooleanMovies" class="series">
                 <h1 class="text-center mt-5 mb-5">Series</h1>
                <ul class="list-inline row row-cols-3 row-cols-md-4 row-cols-lg-5 gap-5 justify-content-center">
                 <Card
                v-for="(series,index) in filmAndMovies.movie" 
                :key="index+'-'+series.id"
                :title="series.name"
                :original="series.original_name"
                :language="series.original_language"
                :vote="series.vote_average"
                :img="series.poster_path"
                :overview="series.overview"
                />
            </ul>
            </div>
            
             <div class="row justify-content-center" v-else-if="valueBooleanMovies == false">
                <div class="col-2">
                    nessuna serie trovata...
                </div>                
            </div>
  </div>
</template>

<script>
import Card from './Card.vue';


export default {
    name:"Main",

    components:{
        Card,
    },

    props: ["filmAndMovies", "valueBooleanFilm", "valueBooleanMovies"],

}
</script>

<style lang="scss">

</style>