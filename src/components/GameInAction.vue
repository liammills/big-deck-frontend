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
        <q-card
          v-ripple
          v-for="card in cards"
          :key="card.message"
          class="q-pa-lg text-h5 card-bg cursor-pointer q-hoverable scroll"
          style="width: 20%; height: 200px; background-color: #c4c4c4"
        >
            {{card.message}}
        </q-card>
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
export default {
  name: 'GameInAction',
  data() {
      return {
          question: "Question with a _____ spot",
          playersRemaining: 4,
          totalPlayers: 8,
          secondsRemaining: 60,
          cards: [
              {message: "You think water moves fast? You should see ice."},
              {message: "Now that there is the Tec-9, a crappy spray gun from South Miami."},
              {message: "Motherfucker do that shit to me, he better paralyze my ass, 'cause I'll kill the motherfucker, know what I'm sayin'?"},
              {message: "Your bones don't break, mine do."},
              {message: "Now that we know who you are, I know who I am."},
              {message: "Look, just because I don't be givin' no man a foot massage"},
              {message: "Some pilots get picked and become television programs."},
          ],
          loadingSubmit: false,
          runTimer: false,
      }
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
      }
  },
  watch: {
    secondsRemaining: {
        handler(value) {
            if (this.runTimer == true && value > 0) {
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
        border: 4px solid #F22771
    .card-bg:active
        border: 4px solid red
</style>