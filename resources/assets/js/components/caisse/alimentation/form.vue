<template lang="html">
  <div class="columns">
    <div class="column">
      <part-panel :editing="editing">
        <div slot="heading">Formulaire d'alimentation</div>
        <div slot="body">
          <form v-on:submit.prevent="onSubmit" @keydown="form.errors.clear($event.target.name)">
            <div class="columns">
                <part-forms-input v-model="form" name="designation" label="Désignation" help="Taper une désignation"></part-forms-input>
                <part-forms-date-picker v-model="form" name="date" label="Date" help="Spécifier une date"></part-forms-date-picker>
                <part-forms-input v-model="form" name="montant" label="Montant" help="Spécifier un montant"></part-forms-input>
                <part-forms-select-full v-model="form" :list="$root.responsables" name="responsable_id" label="Responsable" help="Séléctionner le responsable correspondant"></part-forms-select-full>
            </div>
            <div class="columns is-centered">
              <part-forms-button :editing="editing" ></part-forms-button>
              <part-forms-button-reset></part-forms-button-reset>
            </div>
          </form>
        </div>
      </part-panel>
    </div>
  </div>

</template>

<script>
    import { Form } from './../../../api/form.js';
    export default {
        data(){
          return{
            selected:'',
            form : new Form({
              id:'',
              designation: '',
              date: '',
              montant:'',
              responsable_id: '',
            }),
          }
        },
        computed:{
          editing: function(){
            if (this.$route.params.id) {
              return true
            }else{
              return false
            }
          },
          alimentationId: function(){
            return this.$route.params.id
          }
        },
        created(){
          if (this.alimentationId) {
            axios.get('/alimentations/'+this.alimentationId)
              .then(response => {
                this.form.load(response.data);
            });
          }
        },

        methods: {
          onSubmit(){
            if (this.form.id == '') {
              this.form.post('/alimentations')
                .then(data => {
                  console.log(data.message);
                  Event.$emit('publish-success-message', data.message);
                  this.$parent.getTotaleAlimentations();
                  this.goback();
                })
                .catch(errors =>{
                  console.log(errors);
                });
            }else{
              this.form.put('/alimentations')
                .then(data => {
                  Event.$emit('publish-success-message', data.message);
                  this.$parent.getTotaleAlimentations();
                  this.goback();
                })
                .catch(errors => {
                  console.log(errors);
                });
            }
          },

          goback(){
              this.$router.go(-1);
          }

        }
    }
</script>

<style lang="css">
</style>
