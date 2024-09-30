<template>
    <v-bottom-navigation
      v-if="$vuetify.breakpoint.smAndDown"
      app
      height="60"
      class="pa-0 btm-bg"
    >
        <v-row
            class="row fill-height align-center flex-nowrap no-gutters justify-center"
        >
            <v-col class="d-flex justify-center col-max-width h-100-percent">
                <v-btn @click="toggleDrawer" icon class="btn-min-height w-100 px-3 py-6-px">
                <v-icon>mdi-menu</v-icon>
                </v-btn>
            </v-col>
            
            <v-col class="d-flex justify-center col-max-width h-100-percent">
                <v-btn @click="goToProfile" icon class="btn-min-height w-100 px-3 py-6-px">
                <v-icon>mdi-cash</v-icon>
                </v-btn>
            </v-col>
            <v-col class="d-flex justify-center col-max-width h-100-percent">
                <v-btn @click="goToMessages" icon class="btn-min-height w-100 px-3 py-6-px">
                <v-icon>mdi-email</v-icon>
                </v-btn>
            </v-col>
            <v-col class="d-flex justify-center col-max-width h-100-percent">
                <v-btn @click="goToSettings" icon class="btn-min-height w-100 px-3 py-6-px">
                <v-icon>mdi-message-text</v-icon>
                </v-btn>
            </v-col>
           
        </v-row>
      
  
      <!-- Navigation Drawer -->
      <v-navigation-drawer
        v-model="drawer"
        fixed
        temporary
        bottom
        class="drawer-from-bottom"
        
      >
        <v-list class="row px-4 no-gutters">
            <v-list-item class="col-12 no-gutters">
            <v-list-item-content class="text-end pb-4 col col-12">
                <v-btn @click="drawer = false" icon rounded class="close-button">
                <v-icon>mdi-close</v-icon>
                </v-btn>
            </v-list-item-content>
            </v-list-item>
          <v-list-item
            class ="col-sm-4 col-6 pb-4 pr-4"
          >
            <v-list-item-content class="btn-bg">
                <v-btn class="w-100 ps-2 pe-0 bt-btn" rounded justify-start>電子</v-btn>
            </v-list-item-content>
          </v-list-item>
          <v-list-item
            class ="col-sm-4 col-6 pb-4"
          >
            <v-list-item-content class="btn-bg">
                <v-btn class="w-100 ps-2 pe-0 bt-btn" rounded justify-start>真人</v-btn>
            </v-list-item-content>
          </v-list-item>
          <v-list-item
            class ="col-sm-4 col-6 pb-4 pr-4"
          >
            <v-list-item-content class="btn-bg">
                <v-btn class="w-100 ps-2 pe-0 bt-btn" rounded justify-start>棋牌</v-btn>
            </v-list-item-content>
          </v-list-item>
          <v-list-item
            class ="col-sm-4 col-6 pb-4"
          >
            <v-list-item-content class="btn-bg">
                <v-btn class="w-100 ps-2 pe-0 bt-btn" rounded justify-start>捕魚</v-btn>
            </v-list-item-content>
          </v-list-item>
          <v-list-item
            class ="col-sm-4 col-6 pb-4 pr-4"
          >
            <v-list-item-content class="btn-bg">
                <v-btn class="w-100 ps-2 pe-0 bt-btn" rounded justify-start>競技</v-btn>
            </v-list-item-content>
          </v-list-item>
          <v-list-item
            class ="col-sm-4 col-6 pb-4"
          >
            <v-list-item-content class="btn-bg">
                <v-btn class="w-100 ps-2 pe-0 bt-btn" rounded justify-start>街機</v-btn>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-bottom-navigation>
  </template>
  
  <script>
  export default {
    data() {
      return {
        drawer: false,
        
      };
    },
    methods: {
      toggleDrawer() {
        this.drawer = !this.drawer;
        console.log('toggle')
      },
      goToProfile() {
        // 導航到個人頁面
      },
      goToMessages() {
        // 導航到消息頁面
      },
      goToSettings() {
        // 導航到設定頁面
      },
      selectItem(item) {
        console.log('選擇的項目: ', item.title);
        this.drawer = false; // 點擊後關閉抽屜
      },
    },
  };
  </script>
  
  <style scoped>
  .drawer-from-bottom {
    max-height: 100vh; /* 佔滿螢幕 */
    width: 100vw; /* 全螢幕寬度 */
    position: fixed;
    top: 0;
    left: 0;
    transition: all 0.3s ease;
    z-index: 1000;
    margin-top: 56x;
    }
    .close-button {
    position: absolute !important;
    top: 0px; /* 調整為你需要的距離 */
    right: 0px; /* 調整為你需要的距離 */
    z-index: 1001; /* 確保關閉按鈕在抽屜之上 */
    }
    .v-list-item__content {
        padding: 0;
        height: 56px;
        
    }
    .btn-bg{
        background-color: #e9b950;
        border-radius: 15px;
    }
    .bt-btn .v-btn__content{
    color: #1a0508 !important;
    font-size: 1rem !important;
    font-weight: bolder !important;
}
    .btm-bg{
        background: linear-gradient(180deg, #8f071b, #500001);
    }
</style>
  