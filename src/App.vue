<template>
  <post-form
    @create="createPost"
  />
  <post-list
    :posts=posts
  />

  
</template>

<script>
import PostForm from '@/components/PostForm.vue'
import PostList from '@/components/PostList.vue'


export default {
  name: 'App',
  components: {PostForm, PostList},
  data(){
    return{
      posts:[
        {id: 1, title:"Post 1", body:"Description 1"},
        {id: 2, title:"Post 2", body:"Description 2"},
        {id: 3, title:"Post 3", body:"Description 3"},
        {id: 4, title:"Post 4", body:"Description 4"},
      ],
      
    }
  },
  methods:{
    createPost(post){
      this.posts.push(post)
    },
  },
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 800px;
  color: #2c3e50;
  margin: 0 auto;
}



</style>
