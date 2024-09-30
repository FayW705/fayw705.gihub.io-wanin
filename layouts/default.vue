<template>
  <v-app>
    
    <AppBar @toggleDrawer="toggleDrawer" />
    <NavigationDrawer v-if="$vuetify.breakpoint.mdAndUp" :drawer="drawer" :mini-variant.sync="miniVariant" />
    
    <v-main>
      <v-container fluid>
        <Carousels/>
        <Played />
        <Game/>
      </v-container>
      <Footer />
    </v-main>
    <BottomNav />
  </v-app>
</template>

<script>
import AppBar from '~/components/AppBar.vue'
import NavigationDrawer from '~/components/NavigationDrawer.vue';
import BottomNav from '~/components/BottomNav.vue'
import Carousels from '~/components/Carousels.vue';
import Played from '~/components/Played.vue'
import Game from '~/components/Game.vue';
import Footer from '~/components/footer.vue';

export default {
  components:{
    AppBar,
    NavigationDrawer,
    BottomNav,
    Carousels,
    Played,
    Game,
    Footer
  },
  data() {
    return{
      drawer:true,
      miniVariant:true
    };
  },
  methods:{
    toggleDrawer(){
      this.miniVariant = !this.miniVariant;
    }
  }
};

</script>