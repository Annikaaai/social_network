<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/login" @authenticate="authenticateUser(user)">Login</router-link>
  </nav> -->
  <!-- <RightNav/> -->
  <router-view v-on:login="UpdateUser"/>


  <v-card>
      <v-layout>
        <v-navigation-drawer
          permanent
          location="right"
        >
          <template v-slot:prepend>
            <v-list-item
              lines="two"
              prepend-avatar="https://randomuser.me/api/portraits/women/82.jpg"
              title="Jane Smith"
              subtitle="Logged in"
            ></v-list-item>
          </template>
          <v-divider></v-divider>
          <v-list density="compact" nav class = "navigation">
            <div v-if="login" class = "navigation_item"><router-link to="/login">Login</router-link></div>
            <div v-if="login" class = "navigation_item"><router-link to="/register">Register</router-link></div>

            <div v-if="auth" class = "navigation_item"><router-link to="/">News</router-link></div>
            <div  v-if="auth" class = "navigation_item" ><router-link to="/my_page">My page</router-link></div>
            <div v-if="auth" class = "navigation_item"><router-link to="/friends">Friends</router-link></div>
          </v-list>
        </v-navigation-drawer>
      </v-layout>
  </v-card>

</template>
<script>
// import RightNav from './components/RightNav.vue'
export default {
  name: 'App',
  components: {
    // RightNav
  },
  data(){
    return {auth : false, login : true}
  },
  methods: {

    UpdateUser(){
      this.auth = true;
      this.login = false;

      // alert("Hello")
      // document.getElementById('#nav-item').classList.remove('.nav_display_none');
      //             document.getElementById('#nav-item').classList.add('.nav_display_block');

      //             document.getElementById('#nav_item_login').classList.remove('.nav_display_block');
      //             document.getElementById('#nav_item_login').classList.add('.nav_display_none');
    },
    // ,
  // authenticateUser(user){
  //   this.axios({
  //       method: 'get',
  //       url: 'https://65bdfc43dcfcce42a6f1aab3.mockapi.io/users/api/users',
  //   }).then((response) => { // выполняется в случае успешной отправки
  //       console.log(response);
  //       this.getUserData(); // После отправки сообщения обновляем сообщения снова
  //     })},
  mounted() {
    // хук для первичной загрузки метода
    // this.getUserData();
  }
}
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
nav div.router-link-exact-active{
  background: #2c3e50;
}
.navigation{
  display: block;
}
.navigation_item{
  background: #eaeaea;
  padding: 10px;
  margin: 10px;
  width: 100%;
}
.nav_display_block{
  display: block;
}
.nav_display_none{
  display: none;
}
</style>
