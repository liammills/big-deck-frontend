<template>
  <q-layout>

    <Header />

    <q-page-container>
        <div class="q-mt-xl flex items-center column q-gutter-lg">
            <span class="text-h2" style="font-family: 'Luckiest Guy', cursive; font-size: 46px">
                Join a game
            </span>
            <q-input
                rounded
                standout
                v-model="gameIdInput"
                color="white"
                bg-color="primary"
                label="Game ID"
                style="width: 300px; font-size: 18px"
            />
        <q-input
                rounded
                standout
                v-model="nameInput"
                color="white"
                bg-color="primary"
                label="Name"
                style="width: 300px; font-size: 18px"
            />
        <q-btn
            rounded
            :loading="loadingSubmit"
            color="primary"
            label="Join"
            dense
            push
            v-ripple
            @click="$router.push('lobby')"
            style="font-family: 'Luckiest Guy', cursive; font-size: 26px; padding-top: 12px; margin-top: 200px"
            class="text-h6 q-mt-xl q-px-xl"
        />
    </div>
    </q-page-container>
  </q-layout>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
  name: 'JoinGame',
  components: {
    Header,
  },
  data() {
      return {
          gameId: null,
          name: null,
      }
  },
  computed: {
    gameIdInput: {
      get() {
        return this.gameId;
      },
      set(value) {
        this.gameId = value;
        this.loadSearchResults(); // TO UPDATE
      },
    },
    nameInput: {
      get() {
        return this.name;
      },
      set(value) {
        this.name = value;
        this.loadSearchResults(); // TO UPDATE
      },
    },
  },
//   methods: {
//       joinGame() {
//           console.log('join game')
//       }
//   }
}
</script>
