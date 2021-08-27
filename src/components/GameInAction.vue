<template>
  <q-page class="q-mt-xl flex flex-center column">
    <div class="">
        <div class="text-h2 q-mb-xl q-mt-xl">
            {{question}}
        </div>
        <div v-if="totalPlayers" class="text-h4 flex column text-center q-mb-xl">
            <span>{{playersRemaining}}/{{totalPlayers}} players done</span>
            <span>{{secondsRemaining}} seconds remaining</span>
        </div>
    </div>
    <div class="q-my-xl flex q-gutter-xl items-center justify-center content-center">
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

    <q-btn outline rounded color="primary" label="Submit" style="width: 300px" class="text-h6 q-mt-lg q-mx-auto q-mb-auto" />
    
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
          ]
      }
  }
}
</script>

<style lang="sass">
    .card-bg
        border: 4px solid transparent
    .card-bg:hover
        border: 4px solid #F22771
    .card-bg:active
        border: 4px solid red
</style>