<template>

    <q-card
        v-ripple
        class="q-pa-lg text-h5 card-bg cursor-pointer q-hoverable scroll"
        style="width: 20%; height: 200px"
        :style="isClicked ? { 'background-color': '#7FD877' } : { 'background-color': '#c4c4c4' }"
    >
        {{message}}
    </q-card>

    <!-- @click="changeMe" -->
</template>

<script>
export default {
  name: 'GameCard',
  props: {
      isClicked: {
          type: Boolean,
          default: false,
      },
      message: {
          type: String,
          default: ''
      },
  },
//   data() {
//       return {
//           isClicked: false,
//       }
//   },
//   methods: {
//       changeMe() {
//         this.isClicked = !this.isClicked;
//       }
//   },
}
</script>