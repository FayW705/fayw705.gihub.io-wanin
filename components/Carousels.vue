<template>
   <v-container fluid>
        <v-row class="pa-4 pa-md-6 px-lg-0 px-xl-0 no-gutters justify-center">
            <v-col class="col-lg-9 col-12">
            <v-carousel
                height="264"
                :show-arrows="false"
                cycle
                hide-delimiters
            >
                <v-carousel-item
                v-for="(slide, i) in slides"
                :key="i"
                >
                <v-sheet
                    :color="colors[i]"
                    height="100%"
                >
                    <div class="d-flex fill-height justify-center align-center">
                    <div class="text-h2">
                        {{ slide }} Slide
                    </div>
                    </div>
                </v-sheet>
                </v-carousel-item>
            </v-carousel>
            </v-col>
        </v-row>
   </v-container>
</template>
<script>
export default {
    data () {
      return {
        colors: [
          'indigo',
          'warning',
          'pink darken-2',
          'red lighten-1',
          'deep-purple accent-4',
        ],
        slides: [
          'First',
          'Second',
          'Third',
          'Fourth',
          'Fifth',
        ],
      }
    },
  }
</script>