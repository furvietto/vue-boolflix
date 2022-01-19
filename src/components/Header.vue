.<template>
  <div class="container-fluid">
      <div class="row justify-content-end">
          <div class="col-3">
              <input v-model="inputValue" type="text">
              <button @click="getAxios">INVIA</button>
              <!-- $emit('sendSelect', inputValue) -->
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
        }
    },
    methods: {
      getAxios: function () {
           axios.get("https://api.themoviedb.org/3/search/movie?api_key=53982486ea69d909f7fc01dea5daec6b",
            {
                params: {
                    query: this.inputValue
                }
            })
           .then(res => {
               this.getFilm = res.data.results
                this.$emit("sendSelect", this.getFilm)
              
           })
           .catch(err => {
               console.error(err);               
           })
       }
    },
}
</script>

<style>

</style>