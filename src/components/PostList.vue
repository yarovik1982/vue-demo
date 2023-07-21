<template>
  <div class="posts">
    <h3>Список постов</h3>
    <post-item v-for="post in posts" 
      :key="post.id"
      :post="post"
      @removePost="$emit('removePost', post)"
    />
  </div>
</template>
<script>
import PostItem from '@/components/PostItem.vue'
export default {
   name:'post-list',
  components: {PostItem},
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


</style>
