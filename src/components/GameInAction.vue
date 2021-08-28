<template>
  <q-page class="q-mt-lg flex flex-center column">
      <div class="row full-width text-center items-center q-mt-md">
        <div class="col">
            <q-knob
                show-value
                readonly
                font-size="14px"
                v-model="secondsRemaining"
                size="70px"
                :thickness="0.22"
                max='60'
                color="secondary"
                track-color="grey-3"
                class="q-ma-md"
                >
                {{ secondsRemaining }}
            </q-knob>
            <q-knob
                show-value
                readonly
                font-size="14px"
                v-model="playersRemaining"
                size="70px"
                :thickness="0.22"
                :max=totalPlayers
                color="primary"
                track-color="grey-3"
                class="q-ma-md"
                >
                {{playersRemaining}}/{{totalPlayers}}
            </q-knob>
        </div>
        <div class="col-6">
            <div class="text-h2 q-mb-lg q-mt-xs">
                {{question}}
                <!-- <span v-if="chosenCard" class="text-italic text-h3">{{chosenCard.message}}</span> -->
            </div>
        </div>
        <div class="col q-gutter-lg">
            <q-icon
                name="leaderboard"
                color="blue-grey-6"
                size=36px
                class="cursor-pointer"
            />
            <q-icon
                name="settings"
                color="blue-grey-6"
                size=36px
                class="cursor-pointer"
            />
        </div>
    </div>

    <div class="q-my-md flex q-gutter-xl items-center justify-center content-center">
        <GameCard
          v-for="card in cards"
          :key="card.message"
          style="width: 20%; height: 200px"
          :message="card.message"
          :isClicked="chosenCard.message === card.message ? true : false"
          @click="chosenCard = card"
        />
    </div>

    <q-btn
        rounded
        :loading="loadingSubmit"
        color="primary"
        label="Submit"
        @click="simulateProgress()"
        style="width: 300px; font-family: 'Luckiest Guy', cursive; font-size: 32px; padding-top: 12px;"
        class="text-h6 q-mt-xl q-mx-auto q-mb-xl"
    />
    
  </q-page>

</template>

<style>
</style>

<script>
import GameCard from './GameCard.vue';

export default {
  name: 'GameInAction',
  components: {
    GameCard,
  },
  data() {
      return {
          question: "Two things in life are inevitable. Death and ______",
          playersRemaining: 4,
          totalPlayers: 8,
          secondsRemaining: 60,
          cards: [
              {message: "A cold and indifferent universe", id: 1},
              {message: "Antidepressants"},
              {message: "Winning SYNCS HACK"},
              {message: "White people"},
              {message: "Listening to her problems without trying to solve them"},
              {message: "Getting married, having a few kids, buying some stuff, retiring to Florida, and dying."},
              {message: "Former president George W Bush"},
          ],
          chosenCard: {
              message: null,
          },
          loadingSubmit: false,
          runTimer: false,
      }
  },
  mounted() {
      this.runTimer = true;
  },
  methods: {
      simulateProgress () {
        this.loadingSubmit = true;
        setTimeout(() => {
            this.loadingSubmit = false
        }, 3000)
        this.startTimer();
      },
      startTimer() {
          this.runTimer = true;
      },
  },
  watch: {
    secondsRemaining: {
        handler(value) {
            if (value > 0) {
                // (this.runTimer == true) && 
                setTimeout(() => {
                    this.secondsRemaining--;
                }, 1000);
            }
        },
        immediate: true // This ensures the watcher is triggered upon creation
    }
}
}
</script>

<style lang="sass" scoped>
    @import url('https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap')
    .card-bg
        border: 4px solid transparent
    .card-bg:hover
        border: 4px solid #7FD877
</style>