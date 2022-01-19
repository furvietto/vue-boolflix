.<template>
   <li class="card col">
    <div>TITLE: {{title}}</div>
    <div>
    TITOLO ORIGINALE: {{original}}
    </div>
    <div>
        LINGUA: {{language}}
    </div>
    <div>
        VOTO FINALE: {{vote}}
    </div>  
</li>
</template>

<script>
export default {
    name:"Card",

    props: ["title","original","language","vote"]
}
</script>

<style>

</style>