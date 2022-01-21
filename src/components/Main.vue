.<template>
  <div class="container">      
            <ul v-if="valueBooleanFilm" class="list-inline row row-cols-6 gap-3 justify-content-center">
                <h1 class="text-center text-light col-12">Movies</h1>
                <Card
                v-for="(film,index) in filmAndMovies.films" 
                :key="index+ '-' +film.id"
                :title="film.title"
                :original="film.original_title"
                :language="film.original_language"
                :vote="film.vote_average"
                :img="film.poster_path"
                />
            </ul>
            <div class="row justify-content-center" v-else-if="valueBooleanFilm == false">
                <div class="col-2 text-white">
                    nessun film trovato...
                </div>                
            </div>
            
            <ul v-if="valueBooleanMovies" class="list-inline row row-cols-6 gap-3 justify-content-center">
                <h1 class="text-center text-light col-12">Series</h1>
                 <Card
                v-for="(series,index) in filmAndMovies.movie" 
                :key="index+'-'+series.id"
                :title="series.name"
                :original="series.original_name"
                :language="series.original_language"
                :vote="series.vote_average"
                :img="series.poster_path"
                />
            </ul>
             <div class="row justify-content-center" v-else-if="valueBooleanMovies == false">
                <div class="col-2 text-white">
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