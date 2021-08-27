<template>
  <q-layout>

    <Header />

    <q-page-container class="flex flex-center">
      <q-btn
        rounded
        color="primary"
        label="Login"
        @click="$router.push('game')"
        style="width: 300px; font-family: 'Luckiest Guy', cursive; font-size: 32px; padding-top: 12px;"
        class="text-h6 q-mt-lg q-mx-auto q-mb-xl"
    />
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
