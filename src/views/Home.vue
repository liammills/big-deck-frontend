<template>
  <q-layout>

    <Header />

    <q-page-container class="fixed-center" style="padding: 0;">
      <!-- <div class="full-height items-center flex flex-center"> -->
        <q-btn
          rounded
          push
          v-ripple
          color="primary"
          label="Create a game"
          @click="$router.push('lobby')"
          style="width: 300px; font-family: 'Luckiest Guy', cursive; font-size: 32px; padding-top: 12px;"
          class="text-h6 q-mr-xl"
      />
      <q-btn
          rounded
          outline
          push
          v-ripple
          color="primary"
          label="Join a game"
          @click="$router.push('join')"
          style="width: 300px; font-family: 'Luckiest Guy', cursive; font-size: 32px; padding-top: 12px; border-width: 5px;"
          class="text-h6 q-ml-xl"
      />
      <!-- </div> -->
    </q-page-container>
  </q-layout>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
  name: 'Home',
  components: {
    Header,
  },
}
</script>
