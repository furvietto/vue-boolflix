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
        if (this.inputValue != "") {
              axios.get("https://api.themoviedb.org/3/search/movie?api_key=53982486ea69d909f7fc01dea5daec6b",
            {
                params: {
                    query: this.inputValue
                }
            })
           .then(res => {
               this.getFilm = res.data.results
                this.$emit("sendFilms", this.getFilm)
 
           })
           .catch(err => {
               console.log(err);
          
           })
          }          
       },

    getSeries: function () {
        if (this.inputValue != "") {
              axios.get("https://api.themoviedb.org/3/search/tv?api_key=53982486ea69d909f7fc01dea5daec6b&language=it_IT",
            {
                params: {
                    query: this.inputValue
                }
            })
           .then(res => {
               this.getTvSeries = res.data.results
                this.$emit("sendMovies", this.getTvSeries)
 
           })
           .catch(err => {
               console.log(err);
          
           })
          }          
       },
    },

    

   
}
</script>

<style>
    
</style>