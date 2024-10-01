<template>
  <v-container fluid>
    <v-row class="pa-4 pa-md-6 px-lg-0 px-xl-0 no-gutters justify-center">
      <v-col class="col-lg-9 col-12">
        <v-row class="no-gutters align-center">
          <span class="font-weight-bold text-h5 gradient-primary--text custom-text-noto mr-2 mr-sm-4">
            真人Live
          </span>
          <v-row class="gradientDivider mr-4 no-gutters align-center">
            <svg viewBox="0 0 10 10" width="13" class="squareColor">
              <path d="M5.5,0l-5,5l5,5L10,5.5v-1L5.5,0z M5.5,8.6L1.9,5l3.6-3.6L9.1,5L5.5,8.6z"></path>
            </svg>
            <v-divider></v-divider>
          </v-row>
          <v-btn outlined class="my-2">
            探索全部
          </v-btn>
        </v-row>
      </v-col>
    </v-row>

    <v-row class="pa-4 pa-md-6 px-lg-0 px-xl-0 no-gutters justify-center">
      <v-col class="col-lg-9 col-12">
        <v-sheet class="mx-auto" elevation="1">
          <v-slide-group
            v-model="model"
            class=""
            active-class="ya"
            show-arrows
          >
            <v-slide-item
              v-for="(game, id) in game"
              :key="game.id"
              v-slot="{ active, toggle }"
            >
              <v-card
                :color="active ? undefined : 'grey lighten-1'"
                class="ma-4 my-0"
                width="165"
                height="165"
                @click="toggle"
              >
                <v-row class="fill-height pt-4" align="center" justify="center">
                  <v-scale-transition>
                    <span>{{ game.title }}</span>
                  </v-scale-transition>
                </v-row>

                <!-- 按鈕只在 active 狀態時顯示 -->
                <v-row v-if="active" justify="center" class="mt-4 game-hover">
                  <v-btn color="primary" @click.stop="playGame(id)">
                    遊玩
                  </v-btn>
                </v-row>
              </v-card>
            </v-slide-item>
          </v-slide-group>
        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      model: null,
      game: [
        { id: 1, title: 'game 1' },
        { id: 2, title: 'game 2' },
        { id: 3, title: 'game 3' },
        { id: 4, title: 'game 4' },
        { id: 5, title: 'game 5' },
        { id: 6, title: 'game 6' },
        { id: 7, title: 'game 7' },
        { id: 8, title: 'game 8' },
        { id: 9, title: 'game 9' },
        { id: 10, title: 'game 10' },
        { id: 11, title: 'game 11' },
        { id: 12, title: 'game 12' },
        { id: 13, title: 'game 13' },
        { id: 14, title: 'game 14' },
        { id: 15, title: 'game 15' }
      ]
    };
  },
  methods: {
    playGame(index) {
    const game = this.game[index];
    this.storePlayedGame(game);
    
    // 確認觸發事件
    this.$root.$emit('updatePlayedGames');
  },
  storePlayedGame(game) {
  const playedGames = JSON.parse(localStorage.getItem('playedGames')) || [];
  
  // 檢查是否已經遊玩過該遊戲
  const existingIndex = playedGames.findIndex(g => g.id === game.id);
  if (existingIndex > -1) {
    // 如果已存在，將其從陣列中刪除
    playedGames.splice(existingIndex, 1);
  }
  
  // 將新遊戲放到陣列的最前面
  playedGames.unshift({ id: game.id, title: game.title });
  localStorage.setItem('playedGames', JSON.stringify(playedGames));
  },
  updatePlayedGames() {
    this.$root.$emit('updatePlayedGames');
  }
  }
};
</script>


<style scoped>
.v-sheet {
  box-shadow: none !important;
  border: none;
  background-color: unset;
}
.game-hover{
  position: absolute;
  top: calc(50% - 36px);
  left: calc(50% - 18px);
  opacity: 1;
  background-color: rgba(0,0,0,0.5);
}
</style>
