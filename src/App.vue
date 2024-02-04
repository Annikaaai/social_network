<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/login" @authenticate="authenticateUser(user)">Login</router-link>

  </nav>
  <router-view/>
</template>
<script>
// import LoginComp from './components/LoginComp.vue'
export default {
  name: 'App',
  components: {
    // LoginComp
  },
  data: () => ({
    
  }),
  methods: {
    authenticateUser(user){
      console.log('I am here')
        this.axios.get('https://65bdfc43dcfcce42a6f1aab3.mockapi.io/users/api/users') 
        .then(
          (response) => {
          let users = response.data;
          let found = false;
          for(let index in users){
              if(user.login == users[index].login && user.password == users[index].password){
                  this.$router.push('/users/' + this.myId);
                  found = true;
                  break;
              }
              if(!found){
                window.alert('Неверный логин или пароль')
              }
            }
          }
        )

  },
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
</style>
