<template>
  <div class="posts"
   v-if="posts.length > 0"
  >
  <transition-group name="post">
    <post-item v-for="post in posts"
      :key="post.id"
      :post="post"
      @removePost="$emit('removePost', post)"
    />
  </transition-group>
  </div>
  <h2 v-else style="color:red;margin-top:24px; text-align:center;">
    Список постов пуст ...
  </h2>
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
.post-enter-active,
.post-leave-active {
  transition: all 0.5s ease;
}
.post-enter-from,
.post-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

</style>
