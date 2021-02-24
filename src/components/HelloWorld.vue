<template>
  <v-container class="container-full">
    <v-row class="text-center fill-height align-center">
      <v-col cols="12" class="my-2 text-right">
        <v-switch
                v-model="language"
                label="English"
        ></v-switch>
      </v-col>
      <v-col class="container-full">
        <v-btn
                fab
                class="button"
                color="green"
                @click="sayYes"
        >
          <v-icon color="white" size="160">
            mdi-check
          </v-icon>
        </v-btn>
        <p class="text py-2">
          {{ yes }}
        </p>
      </v-col>
      <v-col class="container-full">
        <v-btn
                fab
                class="button"
                color="red"
                @click="sayNo"
        >
          <v-icon color="white" size="160">
            mdi-close
          </v-icon>
        </v-btn>
        <p class="text py-2">
          {{ no }}
        </p>
      </v-col>
    </v-row>
    <div v-show="false">
      <audio ref="audioYes" :src="yesSound" preload="auto"></audio>
      <audio ref="audioNo" :src="noSound" preload="auto"></audio>
    </div>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      language: false
    }),

    computed: {
      yes() {
        return this.language ? 'Yes' : 'Да'
      },
      no(){
        return this.language ? 'No' : 'Нет'
      },
      yesSound(){
        return this.language ? '/En-uk-yes.ogg' : '/Ru-yes.ogg'
      },
      noSound(){
        return this.language ? '/En-uk-no.ogg' : '/Ru-no.ogg'
      }
    },
    methods: {
      sayYes() {
        this.$refs.audioYes.play()
      },
      sayNo() {
        this.$refs.audioNo.play()
      }
    }
  }
</script>
<style>
  .button {
    max-height: 280px !important;
    max-width: 280px !important;
    min-width: 150px !important;
    min-height: 150px !important;
    height: 100% !important;
    width: 100% !important;
  }

  .container-full {
    height: 100% !important;
  }

  .text {
    font-size: 2em;
  }
</style>
