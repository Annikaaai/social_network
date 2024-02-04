<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Поможем вам зарегистрироваться
            </v-card-title>

            <v-text-field
                label="Придумайте логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Придумайте пароль"
                v-model="password"
                outlined
            ></v-text-field>

            <v-btn @click="authenticateUser()">
                Регистрация
            </v-btn>
        </v-card>
    </div>
</template>
<script>
export default {
  name: 'RegisterPage',
    data: () => ({
    login: "",
    password: ""
  }),
  methods: {
    registerUser(){
        this.axios({
        method: 'post',
        url: 'https://65bdfc43dcfcce42a6f1aab3.mockapi.io/users/api/users',
        data: {
          login: this.login,
          password: this.password
        }
      })

  }

  },
}
</script>