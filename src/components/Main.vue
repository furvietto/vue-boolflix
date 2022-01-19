.<template>
  <div class="container">
      <div class="row">
          <div class="col">
              <ul>
                  <li
                  v-for="(film,index) in inputHeader" 
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

export default {
    name:"Main",

    props: ["inputHeader"],

    data() {
        return {
           
        }
    },

    created() {
      
    },
    methods: {
         
    },
}
</script>

<style>

</style>