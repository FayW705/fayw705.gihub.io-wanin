<template>
    <v-row class="h-100-percent justify-space-between align-end no-gutters">
          <v-container fluid class="pa-0">

            <v-row v-if="playedGames.length > 0" class="pa-4 pa-md-6 px-lg-0 px-xl-0 no-gutters justify-center">
              <v-col class="col-lg-9 col-12">
                <h2 class="font-weight-bold text-h5 mb-4">最近遊玩過的遊戲</h2>
                <v-sheet class="mx-auto" elevation="1">
                    <v-slide-group>
                        <v-slide-item
                        v-for="(game, index) in playedGames"
                        :key="game.id"
                        
                        >
                        <v-card
                            color="grey lighten-1"
                            class="ma-4 my-0"
                            width="165"
                            height="165"
                        >
                            <v-row class="fill-height pt-4" align="center" justify="center">
                            <v-scale-transition>
                                <span>{{ game.title }}</span>
                            </v-scale-transition>
                            </v-row>

                            
                        </v-card>
                        </v-slide-item>
                    </v-slide-group>
                    </v-sheet>
              </v-col>
            </v-row>

            <v-row v-else class="text-center mb-md-10 mb-6 no-gutters justify-center">
              <v-col class="pg-lg-0 px-md-6 px-4 mw-75-v col-lg-9 col-12">

                <v-container fluid>
                  <v-row class="no-gutters">
                    <v-col class="pa-0 col-12">
                      <div class="pa-0 my-4 my-md-6">
                        <span class="font-weight-bold grey-3--text custom-text-noto text-caption">
                          即刻登入，讓星寶為您紀錄近期的遊玩足跡吧！
                        </span>
                      </div>
                    </v-col>
                  </v-row>
                </v-container>

                
              </v-col>
            </v-row>

          </v-container>
        </v-row> 
</template>
<script>
export default {
  data() {
    return {
      playedGames: [] // 將 playedGames 定義為 data 屬性
    };
  },
  mounted() {
    this.loadPlayedGames(); // 載入遊玩過的資料

    // 監聽更新事件
    this.$root.$on('updatePlayedGames', this.loadPlayedGames);
  },
  methods: {
    loadPlayedGames() {
    const storedGames = JSON.parse(localStorage.getItem('playedGames')) || [];
    console.log('載入的遊玩過的遊戲：', storedGames);
    this.playedGames = storedGames;
    }
  },
  beforeDestroy() {
    // 移除事件監聽
    this.$root.$off('updatePlayedGames', this.loadPlayedGames);
  }
};
</script>
<style scoped>
.v-sheet {
  box-shadow: none !important;
  border: none;
  background-color: unset;
}
h2{
    color: #f7b675;
}
</style>