<template>
  <div class="bg-dark border border-success p-4 mb-4">
    <img :src="user.picture.large" alt="" class="user_img rounded-circle" />
    <h6 class="mt-4">{{ user.name.first }} {{ user.name.last }}</h6>
    <p class="small">
      {{ user.email }}
    </p>
    <p class="small">{{ user.location.state }}, {{ user.location.country }}</p>
    <button
      class="btn btn-success"
      data-toggle="modal"
      data-target="#exampleModal"
      @click="showUser"
    >
      View
    </button>
  </div>
</template>

<script>
// console.log(Modal)
export default {
  data() {
    return {
    };
  },
  props: ["user"],
  methods: {
    showUser: function(){
      this.$emit('userDetail', this.user);
    },
  },
};
</script>

<style>
.modal-content {
  background-color: #2c3e50 !important;
}
</style>