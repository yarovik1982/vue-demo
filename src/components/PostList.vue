<template>
  <div class="posts">
    <h3>Список постов</h3>
    <div class="post" v-for="post in posts" :key="post.id">
      <h4>Название поста: {{ post.title }}</h4>
      <p>Описание поста: {{ post.body }}</p>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  props:{
   posts:{
         type:Array,
         required:true,
      }
  },
  data() {
    return {
      
    };
  },
  methods: {},
};
</script>
<style scoped>
.posts {
  padding: 16px 24px;
}
h3,h4{
  margin-bottom: 8px;
}
.post {
  padding: 16px;
  border:2px solid teal;
  margin-bottom: 8px;
}

</style>
