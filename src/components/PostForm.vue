<template>
  <form  @submit.prevent>
    <h4>Создать пост</h4>
      <app-input 
      name="title"
      type="text" 
      v-model="post.title"  
      autocomplete="off"
    />
    <app-input
      name="body"
      type="text" 
      v-model="post.body"  
      autocomplete="off"
   />
    <app-button 
      type="submit" 
      class="btn-send"
      @click="createPost"
    >Создать</app-button>
  </form>
</template>
<script>
import AppIput from './UI/AppInput.vue';
export default {
   name:'post-form',
  components: {AppIput},
  data() {
    return {
      post:{
         title:'',
         body:'',
      }
    };
  },
  methods: {
   createPost(){
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
         title:'',
         body:'',
      }
   }
  },
};
</script>
<style scoped>
form{
  padding: 16px 24px;
  display: flex;
  flex-direction: column;
}
form *{
  /* display: flex; */
  margin-top: 8px;
}

.btn-send{
  align-self: flex-end;
}

</style>
