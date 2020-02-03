<template>
  <!-- App.vue -->

<v-app app>
  <v-navigation-drawer app v-model="drawer" mobile-break-point="991px">
    <v-list subheader>
        <v-subheader>User's list in room</v-subheader>
  
        <v-list-item
          v-for="u in users"
          :key="u.id"
          @click.prevent
        >
          <v-list-item-content>
            <v-list-item-title>{{u.name}}</v-list-item-title>
          </v-list-item-content>
  
          <v-list-item-icon>
            <v-icon :color="u.id === user.id ? 'primary' : 'grey'">mdi-chat</v-icon>
          </v-list-item-icon>
        </v-list-item>
      </v-list>
  
      <v-divider></v-divider>
  </v-navigation-drawer>

  <v-app-bar app>
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    <v-btn icon @click="exit">
          <v-icon>mdi-arrow-left</v-icon>
        </v-btn>
      <v-toolbar-title>Room's chat </v-toolbar-title>
  </v-app-bar>

  <!-- Sizes your content based upon application components -->
  <v-content>

    <!-- Provides the application the proper gutter -->
   <div style="height:100%">
        <nuxt/>
   </div>

  </v-content>
</v-app>
</template>

<script>
import {mapState, mapMutations} from 'vuex'
export default {
  data:() => ({
    drawer:true
  }),
  computed:mapState(['user','users']),
  methods:{
    ...mapMutations(['clearData']),
    exit(){
      this.$socket.emit('userLeft', this.user.id,()=>{
         this.$router.push('/?message=leftChat')
        this.clearData();
      });
     
    }
  }
};
</script>
