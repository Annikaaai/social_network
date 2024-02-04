<template>
    <MyPage v-bind:login = "login"/>
    <p>{{ login }}</p>
</template>
<script>
import MyPage from '@/components/MyPage.vue'

export default {
  name: 'MyPageView',
  components: {
    MyPage
  },
  data() {
        return {
            id: this.$route.params['id'] ,
    login: "qece",
    password: ""
        }
    },
  watch: {
        $route(toR) {
            this.id = toR.params['id'];
            // подставляем корректный id при каждой загрузке страницы
        }
    },
    methods: {
    authenticateUser(){
        this.axios.get('https://65bdfc43dcfcce42a6f1aab3.mockapi.io/users/api/users') 
        .then(
          (response) => {
          let users = response.data;
          this.login = users[this.id].login;
          }
        )
      }
    },
    mounted(){
        this.authenticateUser();
    }
}

</script>