<template lang="html">
  <div class="columns">
    <div class="column is-three-fifths is-offset-one-fifth"><br><br>
      <article class="message is-danger is-medium">
        <div class="message-header">
          <p>Confirmation de suppression</p>
          <!-- <button class="delete" aria-label="delete"></button> -->
        </div>
        <div class="message-body">
          Etes vous sur de vouloir supprimer cette alimentation?<br><br>
          <div class="columns ">
            <div class="column is-offset-one-third"><br>
              <button type="button" class="button is-danger is-outlined" name="button" @click="deleteAlimentation">Supprimer</button>
              <button type="button" class="button is-danger is-outlined" name="button" @click="cancel">Annuler</button>
            </div>
          </div>
        </div>

      </article>
    </div>
  </div>

</template>

<script>
export default {
  data(){
    return{
      alimentation:'',
    }
  },
  created(){
    this.getAlimentation(this.$route.params.id);
  },

  methods: {
    getAlimentation(id){
      axios.get('/alimentations/'+id)
        .then(response => {
          this.alimentation = response.data;
      });
    },
    deleteAlimentation(){
      axios.delete('/alimentations/'+this.$route.params.id)
          .then(response => {
            this.$parent.getTotaleAlimentations();
            this.$router.go(-1);
          })
          .catch(function(err){
            console.log(err);
          });
    },

    cancel(){
      this.$router.go(-1);
    }
  }
}
</script>

<style lang="css">
</style>
