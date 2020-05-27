<template>
  <div id="app">
    <Naslovnica naslov = "Dohvat podataka" podnaslov="Korištenje podataka"/>
    <PopisNastavnika />
  </div>
</template>

<script>
import Naslovnica from './components/Naslovnica'
import PopisNastavnika from './components/PopisNastavnika'

export default {
  name: 'App',
  components: {
    Naslovnica,
    PopisNastavnika
  }
}
</script>

<style>

</style>
