<template>
  <q-page class="q-mt-xl flex items-center column">
    <div class="flex flex-start column q-mt-lg" style="width: 600px">
        <div class="flex row justify-between items-center">
            <span class="text-h2" style="font-family: 'Luckiest Guy', cursive; font-size: 46px">
                Lobby
            </span>
            <q-knob
                show-value
                readonly
                font-size="14px"
                v-model="users.length"
                size="66px"
                :thickness="0.22"
                :max="totalPlayersPermitted"
                color="secondary"
                track-color="grey-3"
                class="q-ma-md"
                >
                {{users.length}}/{{totalPlayersPermitted}}
            </q-knob>
        </div>
        <div class="flex column scroll no-wrap" style="height: 400px;">
            <span
                v-for="user in users"
                class="text-h5 q-mb-sm"
                :key="user.name"
            >
                {{user.name}}
            </span>
        </div>
    </div>
    
    <q-btn
        rounded
        :loading="loadingSubmit"
        color="primary"
        label="Start game"
        dense
        push
        v-ripple
        :disabled="users.length < 2"
        @click="simulateProgress()"
        style="width: 300px; font-family: 'Luckiest Guy', cursive; font-size: 32px; padding-top: 18px;"
        class="text-h6 q-mt-xl"
    />
  </q-page>

</template>

<style>
</style>

<script>
export default {
  name: 'GameLobby',
  data() {
      return {
          totalPlayersPermitted: 8,
          users: [
              {name: "SamuelLJackson (Host)"},
              {name: "DannyDeVito1"},
              {name: "DannyDeVito2"},
              {name: "DannyDeVito3"},
          ],
      }
  },
}
</script>

<style lang="sass" scoped>
    
</style>