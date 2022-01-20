.<template>
  <div class="container-fluid">
      <div class="row justify-content-end">
          <div class="col-3">
              <input @keyup.enter="getMerge" v-model="inputValue" type="text">
              <button @click="getMerge">INVIA</button>
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
    methods: {
    getMerge: function () {
      this.getMovies();  
      this.getSeries();  
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

<style>
    
</style>