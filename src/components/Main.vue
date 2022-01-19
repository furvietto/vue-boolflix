.<template>
  <div class="container">
      <div class="row">
          <div class="col">
              <ul>
                  <li
                  v-for="(film,index) in getAxios" 
                  :key="index"
                  >
                  <div>{{film.title}}</div>
                  <div>
                      {{film.original_title}}
                  </div>
                    <div>
                        {{film.original_language}}
                    </div>
                  <div>
                      {{film.vote_average}}
                  </div>
                  
                  </li>
              </ul>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name:"Main",

    props: ["inputHeader"],

    data() {
        return {
           getFilm: [], 
           getString: this.inputHeader,
        }
    },

    computed: {
      getAxios: function () {
          if (this.getString != "") {
              axios.get("https://api.themoviedb.org/3/search/movie?api_key=53982486ea69d909f7fc01dea5daec6b",
            {
                params: {
                    query: this.getString
                }
            })
           .then(res => {
               return res.data.results     
           })
           .catch(err => {
              return console.error(err);               
           })
          }
           
       }
    },

}
</script>

<style>

</style>