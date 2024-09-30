<template>
    <v-app-bar
      app
    >
      <v-row class=" no-gutters justify-center">
        <v-col>
          <v-row class="no-gutters align-center">
            <v-app-bar-nav-icon v-if="$vuetify.breakpoint.mdAndUp" @click.stop="$emit('toggleDrawer')" class="mr-lg-6 mr-sm-4 mr-2"/>
            <v-app-bar-title></v-app-bar-title>
            <v-spacer />
            <v-btn class="login-btn">登入</v-btn>
          </v-row>
        </v-col>
      </v-row>
    </v-app-bar>
    
  </template>
  
  <script>
  export default{
    name: 'AppBar',
  };
  </script>