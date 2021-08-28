<template>
  <q-layout>

    <Header v-if="loading" />
    <Header v-else id="7FD877" />

    <q-page-container v-show="!loading">
      <!-- <GameInAction v-if="started" /> -->
      <GameLobby />
    </q-page-container>

    <q-inner-loading :showing="loading" >
        <q-spinner-puff size="100px" color="primary" />
    </q-inner-loading>
  </q-layout>
</template>

<script>
import Header from '@/components/Header.vue'
// import GameInAction from '@/components/GameInAction.vue'
import GameLobby from '@/components/GameLobby.vue'

export default {
  name: 'Game',
  components: {
    // GameInAction,
    Header,
    GameLobby,
  },
  data() {
    return {
      loading: true,
      // started: false,
    }
  },
  async mounted() {
      this.loading = true;
      try {
        await new Promise(r => setTimeout(r, 2500));
      } finally {
        this.loading = false;
      }
  },
  methods: {
  }
}
</script>
