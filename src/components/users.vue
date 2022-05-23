<template>
  <div class="container">
    <div class="row mx-0 px-0 p-4">
      <div v-for="user in users" :key="user" class="col col-md-4">
        <User :user="user" @userDetail="show"/>
      </div>
    </div>
  </div>

    <Modal :user="user"/>

  <div class="loading" v-if="fetching">
    <h5>Loading Users...</h5>
    <h5 v-if="error">Error Fetching Users...</h5>
  </div>
</template>

<script>
import axios from "axios";
import User from "./user.vue";
import Modal from './userModal.vue';

export default {
  data() {
    return {
      users: "",
      user: {},
      fetching: false,
      error: false,
    };
  },
  components: {
    User, Modal,
  },
  methods: {
    async getUsers() {
      this.fetching = true;
      try {
        let response = await axios.get("https://randomuser.me/api/?results=10");
        this.users = response.data.results;

        // console.log(this.users);
        this.fetching = false;
      } catch (error) {
        this.error = true;
        console.log(error.response);
      }
    },
    show(user){
      this.user = user
    }
  },
  created() {
    this.getUsers();
  },
};
</script>

<style scoped>
.loading {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>