.<template>
  <div class="container">      
            <ul v-if="valueBooleanFilm" class="list-inline row row-cols-6 gap-3 justify-content-center">
                <h1 class="text-center col-12">Movies</h1>
                <Card
                v-for="(film,index) in filmAndMovies.films" 
                :key="index"
                :title="film.title"
                :original="film.original_title"
                :language="film.original_language"
                :vote="film.vote_average"
                :img="film.poster_path"
                />
            </ul>
            <div class="row justify-content-center" v-else-if="valueBooleanFilm == false">
                <div class="col-2">
                    nessun film trovato...
                </div>                
            </div>
            
            <ul v-if="valueBooleanMovies" class="list-inline row row-cols-6 gap-3 justify-content-center">
                <h1 class="text-center col-12">Series</h1>
                 <Card
                v-for="(series,index) in filmAndMovies.movie" 
                :key="index"
                :title="series.name"
                :original="series.original_name"
                :language="series.original_language"
                :vote="series.vote_average"
                :img="series.poster_path"
                />
            </ul>
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
ul {
    list-style: none;
}
</style>