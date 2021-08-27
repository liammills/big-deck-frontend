<template>
  <q-page :loading="loading" class="q-mt-xl flex flex-center column">
    <div>
        <div class="text-h2 q-mb-lg q-mt-xl">
            {{question}}
        </div>
        <div v-if="totalPlayers" class="text-h4 flex column text-center text-weight-light">
            <span>{{playersRemaining}}/{{totalPlayers}} players done</span>
            <span>{{secondsRemaining}} seconds remaining</span>
        </div>
    </div>
    <q-inner-loading v-if="loading" showing>
        <q-spinner-puff size="xl" color="primary" />
    </q-inner-loading>
    <div class="q-my-md flex q-gutter-xl items-center justify-center content-center">
        <q-card
          v-ripple
          v-for="card in cards"
          :key="card.message"
          class="q-pa-lg text-h5 card-bg cursor-pointer q-hoverable"
          style="width: 20%; height: 200px; background-color: #c4c4c4"
        >
            {{card.message}}
        </q-card>
    </div>

    <q-btn
        rounded
        color="primary"
        label="Submit"
        style="width: 300px; font-family: 'Luckiest Guy', cursive; font-size: 32px; padding-top: 12px;"
        class="text-h6 q-mt-xl q-mx-auto q-mb-xl"
    />
    
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'GameInAction',
  data() {
      return {
          question: "Question with a _____ spot",
          playersRemaining: 4,
          totalPlayers: 8,
          secondsRemaining: 25,
          cards: [
              {message: 'You think water moves fast? You should see ice.'},
              {message: 'Now that there is the Tec-9, a crappy spray gun from South Miami.'},
              {message: 'sfdgdfsadf '},
              {message: 'gfbxbgsry'},
              {message: 'gfbxbgsry'},
              {message: 'gfbxbgsry'},
              {message: 'gfbxbgsry'},
          ],
          loading: true,
      }
  },
  async mounted() {
      this.loading = true;
      try {
        await Promise(this.waitLoad());
      } finally {
        this.loading = false;
      }
  },
  methods: {
      async waitLoad() {
          await new Promise(r => setTimeout(r, 3000));
          console.log('asdoasd'); // TO DELETE
      }
  }
}
</script>

<style lang="sass">
    @import url('https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap')
    .card-bg
        border: 4px solid transparent
    .card-bg:hover
        border: 4px solid #F22771
    .card-bg:active
        border: 4px solid red
</style>