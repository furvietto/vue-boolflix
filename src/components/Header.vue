.<template>
  <div class="container-fluid">
      <div class="row justify-content-between bg-dark">
          <div class="col-3 ">
              <img src="https://cdn.discordapp.com/attachments/895657298859544588/934028535184642078/logo.png" alt="">
          </div>
          <div class="col-3 d-flex align-items-center">
              <input placeholder="inserisci titolo..." class="m-2" @keyup.enter="getMerge" v-model="inputValue" type="text">
              <button class="btn btn-danger" type="button" @click="getMerge">INVIA</button>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';


export default {
    name: "Header",
    data() {
        return {
            inputValue: "",
            getFilm: [], 
            getTvSeries: []
        }
    },
    created() {
        this.getRandomMovie()
        this.getRandomTv()
    },
    methods: {
        getMerge: function () {
        this.getMovies();  
        this.getSeries();  
        },    

        getRandomMovie: function () {
            axios.get('https://api.themoviedb.org/3/discover/movie?api_key=53982486ea69d909f7fc01dea5daec6b&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=flatrate')
            .then(res => {
                this.getFilm = res.data.results
                this.$emit("sendFilms", this.getFilm)
                this.$emit("sendBooleanFilm" , true)
            })
            .catch(err => {
                console.error(err); 
            })
        },

        getRandomTv: function () {
            axios.get('https://api.themoviedb.org/3/discover/tv?api_key=53982486ea69d909f7fc01dea5daec6b&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=flatrate')
            .then(res => {
                this.getTvSeries = res.data.results
                this.$emit("sendMovies", this.getTvSeries)
                this.$emit("sendBooleanMovies", true)
            })
            .catch(err => {
                console.error(err); 
            })
        },

        getMovies: function () {
            
                axios.get("https://api.themoviedb.org/3/search/movie?api_key=53982486ea69d909f7fc01dea5daec6b",
                {
                    params: {
                        query: this.inputValue
                    }
                })
            .then(res => {
                this.getFilm = res.data.results
                if (this.getFilm.length > 0) {
                    this.$emit("sendBooleanFilm" , true)
                    this.$emit("sendFilms", this.getFilm)
                } else {
                    this.$emit("sendBooleanFilm" , false)
                }
            })
            .catch(err => {
                console.log(err);
                    this.$emit("sendBooleanFilm" , false)
            })
                    
        },

        getSeries: function () {
        
                axios.get("https://api.themoviedb.org/3/search/tv?api_key=53982486ea69d909f7fc01dea5daec6b&language=it_IT",
                {
                    params: {
                        query: this.inputValue
                    }
                })
            .then(res => {
                this.getTvSeries = res.data.results
                if (this.getTvSeries.length > 0) {
                    this.$emit("sendMovies", this.getTvSeries)
                    this.$emit("sendBooleanMovies", true)
                } else {
                    this.$emit("sendBooleanMovies", false)
                }
                    

            })
            .catch(err => {
                console.log(err);
                    this.$emit("sendBooleanMovies", false)
            })
                    
        },
    },

    

   
}
</script>

<style lang='scss' scoped>
    .btn{
        padding: 2px 10px;
    }
</style>