.<template>
  <div class="container">      
              <ul v-if="inputError" class="list-inline row row-cols-6 gap-3 justify-content-center">
                  <li
                  class="card col"
                  v-for="(film,index) in inputHeader" 
                  :key="index"
                  >
                  <div>TITLE: {{film.title}}</div>
                  <div>
                    TITOLO ORIGINALE: {{film.original_title}}
                  </div>
                    <div>
                       LINGUA: {{film.original_language}}
                    </div>
                  <div>
                     VOTO FILM: {{film.vote_average}}
                  </div>
                  
                  </li>
              </ul>
              <div v-else>
                  Ricerca non correlata
              </div>
  </div>
</template>

<script>

export default {
    name:"Main",

    props: ["inputHeader","inputError"],

    data() {
        return {
        
        }
    },

    methods: {
        
    },

}
</script>

<style lang="scss">
ul {
    list-style: none;
}
</style>