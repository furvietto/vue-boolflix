
.<template>
<!-- le bandiere sono come fontawesome
<i class="flag flag-us"></i>
al posto di us mettete dinamicamente la lingua che prendete dall'api
come linguaggio c'è 'en' che non ha una bandiera
io ho messo un metodo che viene richiamato sempre
<i :class="'flag flag-' + getFlag(list.original_language)" />
getFlag(lang) {
      if (lang === 'en') {
        return 'us';
      }
      return lang;
    }, -->
   <li class="card col">
    <div>TITLE: {{title}}</div>
    <div>
    TITOLO ORIGINALE: {{original}}
    </div>
    <div>
        LINGUA: <i :class="'flag flag-' + getFlag(language)"></i> 
    </div>
    <div>
        VOTO FINALE: {{vote}}
    </div>  
</li>
</template>

<script>
export default {
    name:"Card",

    methods: {
        getFlag(lang) {
            if (lang === 'en') {
                return 'us';
            }
            return lang;
        },
    },

    props: ["title","original","language","vote"]
    }


</script>

<style>
    @import '~mdb-ui-kit/css/mdb.min.css';
</style>