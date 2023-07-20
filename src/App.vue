<template>
  <form action="#" @submit.prevent="createPost(event)">
    <h4>Создать пост</h4>
    <input 
      type="text"
      :value="title"
      @input="title=$event.target.value"
    >
    <input 
      type="text"
      :value="body"
      @input="body=$event.target.value"
    >
    <button type="submit" class="btn-send">Создать</button>
  </form>

  <div class="posts">
    <h3>Список постов</h3>
    <div class="post"
      v-for="post in posts"
    >
      <h4>Название поста: {{post.title}}</h4>
      <p>Описание поста: {{post.body}}</p>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {},
  data(){
    return{
      posts:[
        {id: 1, title:"Post 1", body:"Description 1"},
        {id: 2, title:"Post 2", body:"Description 2"},
        {id: 3, title:"Post 3", body:"Description 3"},
        {id: 4, title:"Post 4", body:"Description 4"},
      ],
      title:'',
      body: '',
    }
  },
  methods:{
    createPost(event){
      const newPost = {
        id:Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost)
      this.title = ''
      this.body = ''
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
.btn-send{
  align-self: flex-end;
  background-color: transparent;
  border:1px solid teal;
  padding: 4px 8px;
}
</style>
