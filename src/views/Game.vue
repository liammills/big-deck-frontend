<template>
  <q-layout>

    <Header id="7FD877" />

    <q-page-container>
      <GameInAction />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
import Header from '@/components/Header.vue'
import GameInAction from '@/components/GameInAction.vue'

export default {
  name: 'Home',

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
