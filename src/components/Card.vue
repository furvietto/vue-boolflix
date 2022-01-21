
.<template>

   <li class="card col pt-1 pb-1">
    <img v-if="img" :src="'https://image.tmdb.org/t/p/w500' + img" alt="">
    <img v-else src="https://images-ext-2.discordapp.net/external/N_p-FmrdDUA2xojPEDtU9XvZSh8i6ki-3HeCRMMAdwM/https/cdn.download.it/ms/static/images/poster-placeholder.png?width=468&height=700" alt="">
    <div>TITLE: {{title}}</div>
    <div v-show="original != title">
    TITOLO ORIGINALE: {{original}}
    </div>
    <div>
        LINGUA: <i :class="'flag flag-' + getFlag(language)"></i> 
    </div>
    <div>
        VOTO : <i v-for="(n, index) in 5" 
        :key="index" 
        :class="(index < getVote(vote) ? 'fas fa-star' : 'far fa-star')"></i>
    </div>  
    
</li>
</template>

<script>
export default {
    name:"Card",

    data() {
        return {
            decimalNumber: null
        }
    },

    methods: {
        getFlag(lang) {
            switch (lang){
            case 'en':
                return 'us';
            case 'ko':
                return 'kr';
            case 'ja':
                return 'jp';
            case 'ur':
                return 'pk';
            case 'zh':
                return 'cn';
            default:
                return lang
            }
        },

        getVote(vote) { 
           return Math.round(vote / 2) 
        }
    },

    props: ["title","original","language","vote","img"]
    }


</script>

<style>

    @import '~mdb-ui-kit/css/mdb.min.css';
</style>