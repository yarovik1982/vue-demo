<template>
  <form action="#" @submit.prevent>
    <h4>Создать пост</h4>
      <input 
      type="text" 
      v-model="post.title"  
    />
    <input 
      type="text" 
      v-model="post.body"  
   />
    <button type="submit" class="btn-send"
      @click="createPost"
    >Создать</button>
  </form>
</template>
<script>
export default {
   name:'post-form',
  components: {},
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
input{
  width: 100%;
  padding: 4px 16px;
  outline: none;
  border: 2px solid teal;
}
.btn-send{
  align-self: flex-end;
  background-color: transparent;
  border:1px solid teal;
  padding: 4px 8px;
}
</style>
