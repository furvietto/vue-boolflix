.<template>
  <div class="container-fluid">
      <div class="row justify-content-end">
          <div class="col-3">
              <input v-model="inputValue" type="text">
              <button @click="$emit('sendSelect', inputValue)">INVIA</button>
          </div>
      </div>
  </div>
</template>

<script>



export default {
    name: "Header",
    data() {
        return {
            inputValue: "",
        }
    },
    
}
</script>

<style>

</style>