<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>

            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>

            <v-btn @click="authenticateUser()">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>
<script>
export default {
  name: 'LoginComp',
    data: () => ({
    login: "",
    password: ""
  }),
  methods: {
    authenticateUser(){
        this.axios.get('https://65bdfc43dcfcce42a6f1aab3.mockapi.io/users/api/users') 
        .then(
          (response) => {
          let users = response.data;
          let found = false;
          for(let index in users){
              if(this.login == users[index].login && this.password == users[index].password){
                
                  this.$router.push('/my_page/' + users[index].id);
                  console.log(users[index].id)
                  found = true;
                  this.$emit('login', index)

                  break;
              }
              if(!found){
                window.alert('Неверный логин или пароль')
              }
            }
          }
        )

  }


    // auth() {
        
    //   this.$emit('authenticate', { // создаем ивент для того, чтобы App.vue мог получить данные
    //     login: this.login, // отправляем в ивенте данные
    //     password: this.password, // отправляем в ивенте данные
    //   });
    // },
  },
}
</script>