<template>
  <div>
    <b-container>
      <b-row>
        <b-col cols="4">
          <b-form-input v-model="pretraga" placeholder="Podaci o nastavnicima" @keyup.enter="dohvatiPodatke"></b-form-input>
        </b-col>

        <b-col cols="2">
        <b-button @click="dohvatiPodatke">Dohvati podatke</b-button> 
      </b-col>
      </b-row>

      

      <b-row>
        <b-col cols="4" v-for="nastavnik in nastavnici" v-bind:key="'nastavnik_'+nastavnik.o_id">
          <b-card
            :title="nastavnik.o_ime + ''  +nastavnik.o_prezime"
            :img-src="'https:/nastavnici.fpmoz.sum.ba/uploads/' + nastavnik.oo_profilna_slika"
            img-height="220px"
            img-width="150px"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
          >
            <b-card-text>
                {{nastavnik.o_email}}
            </b-card-text>

            <b-button href="#" variant="primary">Dohvati podatke</b-button>
          </b-card>
          <h3></h3>
          <p></p>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "PopisNastavnika",
  data: function() {
    return {
      pretraga: "",
      nastavnici: [] //prazan niz
    };
  },
  methods: {
    dohvatiPodatke: function() {
      this.axios
        .get("https://nastavnici.fpmoz.sum.ba/index.php/profile/search/"+this.pretraga)
        .then(response => {
          console.log(response.data.osoblje);

          this.nastavnici = response.data.osoblje;

          for (let i=0; i< this.nastavnici.length; i++){
              if (this.nastavnici[i].oo_profilna_slika==null) {
                     this.nastavnici[i].oo_profilna_slika='logo_fpmoz.png';
          }
          }
        });
    }
  }
};
</script>

<style>
</style>