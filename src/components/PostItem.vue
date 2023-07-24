<template>
  <div class="post">
    <div style="padding-right:16px;">
      <p>{{post.id}}</p>
      <h4>Название поста: {{ post.title }}</h4>
      <p>Описание поста: {{ post.body }}</p>
    </div>
    <app-button 
      class="btn-delete-post"
      @click="$emit('removePost', post)"
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
