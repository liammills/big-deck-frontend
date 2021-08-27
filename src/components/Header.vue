<template>
    <q-header elevated class="header">
      <q-toolbar class="q-px-xl">

        <q-toolbar-title
            class="q-pa-none cursor-pointer"
            @click="$router.push('/')"
        >
            <div class="logo">
                Big Deck
            </div>
        </q-toolbar-title>

        <div v-if="id">{{id}}</div>
      </q-toolbar>
    </q-header>
</template>

<style>
</style>

<script>
export default {
  name: 'Header',
  props: {
      id: {
          type: String,
      }
  },
}
</script>

<style lang="sass">
  @import url('https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap')
  .header
    font-family: 'Luckiest Guy', cursive
    font-size: 50px
    height: 100px
  .logo
    font-family: 'Luckiest Guy', cursive
    font-size: 80px
    color: #F22771
    padding: 0px
    margin: 0px
</style>
