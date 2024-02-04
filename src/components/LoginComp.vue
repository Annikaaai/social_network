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

            <v-btn @click="auth">
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
    auth() {
        
      this.$emit('authenticate', { // создаем ивент для того, чтобы App.vue мог получить данные
        login: this.login, // отправляем в ивенте данные
        password: this.password, // отправляем в ивенте данные
      });
    },
  },
}
</script>