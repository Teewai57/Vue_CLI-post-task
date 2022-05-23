<template>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <!-- <h5 class="modal-title" id="exampleModalLabel">Modal title</h5> -->
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
         <img :src="user?.picture?.large" alt="" class="user_img rounded-circle"/>
    <h6 class="mt-4"> {{user?.name?.first}} {{user?.name?.last}} </h6>
    <p class="small">
        {{user?.email}}
    </p>
    <p class="small">
        {{user?.location?.state}}, {{user?.location?.country}}
    </p> 
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
    
    <!-- {{user.picture.medium}} -->
</template>

<script>
export default {
  data() {
    return {
      name: 'Modal',
      displayModal: false,
      
    };
  },
  props: ["user"],
  methods: {
    offModal() {
      this.$emit("close");
    },
    // show(e){
    //   console.log(e)
    // }
  },
};
</script>

<style>

</style>