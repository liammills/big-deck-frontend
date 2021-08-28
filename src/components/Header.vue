<template>
    <q-header elevated class="header">
      <q-toolbar class="q-px-xl">

        <q-toolbar-title
            class="q-pa-none"
        >
            <div
                class="logo cursor-pointer"
                @click="$router.push('/')"
            >
                Big Deck
            </div>
        </q-toolbar-title>

        <div
            v-if="id"
            class="cursor-pointer"
            @click="copy"
        >
            <span class="id-text">{{id}}</span>
            <q-popup-proxy>
                <q-banner>
                <template v-slot:avatar>
                    <q-icon name="assignment" color="primary" />
                </template>
                    Game ID copied to clipboard.
                </q-banner>
            </q-popup-proxy>
        </div>
      </q-toolbar>
    </q-header>
</template>

<style>
</style>

<script>
import { copyToClipboard } from 'quasar'

export default {
  name: 'Header',
  props: {
      id: {
          type: String,
      }
  },
  methods: {
      copy() {
        copyToClipboard(this.id)
            .then(() => {
                console.log('id copied');
            })
            .catch((e) => {
                console.log(e);
            })
      }
  }
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
  .id-text:hover
    text-decoration: underline
</style>
