<template>
  <div class="post">
    <div>
      <h4>Название поста: {{ post.title }}</h4>
      <p>Описание поста: {{ post.body }}</p>
    </div>
    <app-button 
      class="btn-delete-post"
      @click="$emit('removePost',   post)"
    >Удалить</app-button>
  </div>
</template>
<script>

export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {};
  },
//   methods: {
//    removePost(post){
//       this.$emit('removePost', this.post)
//    },
//   },
};
</script>
<style scoped>
h3,
h4 {
  margin-bottom: 8px;
}
.post {
  padding: 16px;
  border: 2px solid teal;
  margin-bottom: 8px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
>
