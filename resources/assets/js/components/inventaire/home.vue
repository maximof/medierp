<template lang="html">
  <div>
    <global-pagetitle color="primary" title="Inventaires Manager" subtitle="Caisses et banques" icon="list-alt"></global-pagetitle>
    <br><br>
    <div class="columns is-centered">
      <div class="column is-narrow">
        <part-tile>
          <div slot="body">
            <div class="columns is-centered">
              <div class="column is-narrow">
                <center>
                  <span class="icon is-large">
                    <i class="fa fa-3x fa-list"></i>
                  </span>
                </center><br>
                <p class="title is-4">Inventaire des charges</p>
              </div>
            </div>
            <a class="button is-primary is-inverted is-outlined is-fullwidth" @click="$router.push({ path: `/inventaire/charges` })"><i class="fa fa-list"></i>&nbsp;&nbsp;Liste</a>
          </div>
        </part-tile>
      </div>
      <div class="column is-narrow">
        <part-tile>
          <div slot="body">
            <div class="columns is-centered">
              <div class="column is-narrow">
                <center>
                  <span class="icon is-large">
                    <i class="fa fa-3x fa-list"></i>
                  </span>
                </center><br>
                <p class="title is-4">Inventaire des alimentations</p>
              </div>
            </div>
            <a class="button is-primary is-inverted is-outlined is-fullwidth" @click="$router.push({ path: `/inventaire/alimentations` })"><i class="fa fa-list"></i>&nbsp;&nbsp;Liste</a>
          </div>
        </part-tile>
      </div>
      <div class="column is-narrow">
        <part-tile>
          <div slot="body">
            <div class="columns is-centered">
              <div class="column is-narrow">
                <center>
                  <span class="icon is-large">
                    <i class="fa fa-3x fa-list"></i>
                  </span>
                </center><br>
                <p class="title is-4">Inventaire des encaissements</p>
              </div>
            </div>
            <a class="button is-primary is-inverted is-outlined is-fullwidth" @click="$router.push({ path: `/inventaire/encaissements` })"><i class="fa fa-list"></i>&nbsp;&nbsp;Liste</a>
          </div>
        </part-tile>
      </div>
      <div class="column is-narrow">
        <part-tile>
          <div slot="body">
            <div class="columns is-centered">
              <div class="column is-narrow">
                <center>
                  <span class="icon is-large">
                    <i class="fa fa-3x fa-list"></i>
                  </span>
                </center><br>
                <p class="title is-4">Inventaire des decaissements</p>
              </div>
            </div>
            <a class="button is-primary is-inverted is-outlined is-fullwidth" @click="$router.push({ path: `/inventaire/decaissements` })"><i class="fa fa-list"></i>&nbsp;&nbsp;Liste</a>
          </div>
        </part-tile>
      </div>
    </div>

  </div>
</template>

<script>
export default {
}
</script>

<style lang="css">
</style>
