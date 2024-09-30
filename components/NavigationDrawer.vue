<template>
  <v-navigation-drawer
   
    v-model="drawer"
    app
    :mini-variant="miniVariant" 
    permanent
    :border="true"
  >
    <v-list>
      <v-list-item
        v-for="(item, i) in items"
        :key="i"
        :to="item.to"
        router
        exact
      >
        <v-list-item-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  props: {
    drawer: {
      type: Boolean,
      required: true, 
    },
    miniVariant: {
      type: Boolean,
      required: true, 
    },
  },
  data() {
    return {
      items: [
        { icon: 'mdi-apps', title: '首頁', to: '/' },
        { icon: 'mdi-chart-bubble', title: '電子', to: '/electronics' },
        { icon: 'mdi-chart-bubble', title: '真人', to: '/real' },
        { icon: 'mdi-chart-bubble', title: '期牌', to: '/period' },
        { icon: 'mdi-chart-bubble', title: '捕魚', to: '/fishing' },
        { icon: 'mdi-chart-bubble', title: '競技', to: '/competition' },
        { icon: 'mdi-chart-bubble', title: '街機', to: '/arcade' }
      ]
    };
  }
};
</script>
