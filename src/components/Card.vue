
.<template>

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
        }
    },

    props: ["title","original","language","vote"]
    }


</script>

<style>
    @import '~mdb-ui-kit/css/mdb.min.css';
</style>