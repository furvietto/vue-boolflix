
.<template>

   <li class="text-white position-relative card col pt-1 pb-1">
    <img v-if="img" :src="'https://image.tmdb.org/t/p/w500' + img" alt="">
    <img v-else src="https://images-ext-2.discordapp.net/external/N_p-FmrdDUA2xojPEDtU9XvZSh8i6ki-3HeCRMMAdwM/https/cdn.download.it/ms/static/images/poster-placeholder.png?width=468&height=700" alt="">
    <div class="appear p-3">
        <h4>{{title}}</h4>
        <div class="mb-3" v-show="original != title">
        TITOLO ORIGINALE: {{original}}
        </div>
        <div class="mb-3">
            LINGUA: <i :class="'flag flag-' + getFlag(language)"></i> 
        </div>
        <div class="mb-3">
            VOTO : <i class="text-warning" v-for="(n, index) in 5" 
            :key="index" 
            :class="(index < getVote(vote) ? 'fas fa-star' : 'far fa-star')"></i>
        </div> 
        <div>
            OVERVIEW : {{(overview != "") ? overview : "no description" }}
        </div>
    </div>
     
    
</li>
</template>

<script>
export default {
    name:"Card",

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

    props: ["title","original","language","vote","img","overview"]
    }


</script>

<style lang="scss" scoped>
    @import '~mdb-ui-kit/css/mdb.min.css';
li {
    cursor: pointer;
    &:hover .appear {
        display: block;
    }
     .appear {
        display: none;
        position: absolute;
        top: 0;
        left: 0;
        background-color: rgba($color: #000000, $alpha: 0.6);
        width: 100%;
        height: 100%;
        overflow: auto;
    }
}
   
</style>