<template>
  <q-layout>

    <Header />

    

    <q-page-container>
      <GameInAction />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import GameInAction from './components/GameInAction.vue'

export default {
  name: 'LayoutDefault',

  components: {
    GameInAction,
    Header,
  },

  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>

<style lang="sass">

</style>
