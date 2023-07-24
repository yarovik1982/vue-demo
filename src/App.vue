<template>
  <div>
    <app-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </app-dialog>
    <h1>Страница с постами</h1>
    <app-input
      v-model="searchQuery"
      placeholder="Поиск..."
    />
    <div class="row">
      <app-button  @click="showDialog">Создать пост</app-button>
      <app-select
        v-model="selectedSort"
        :options="sortOptions"
      ></app-select>
    </div>
    <post-list 
      :posts="sortAndSearchPosts"
       @removePost="removePost" 
      v-if="!isPostsLoading" 
    />
    <div v-else class="square">
      <div></div>
      <div></div>
    </div>
    <div class="pagination">
      <div 
      v-for="pageNumber in totalPages" 
      :key="pageNumber"
      class="pagination-item" 
      :class="{'item-current': page === pageNumber}"
      @click="changePage(pageNumber)"
      >
      {{pageNumber}}
      </div>
    </div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import axios from "axios";

export default {
  name: "App",
  components: { PostForm, PostList},
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort:'',
      searchQuery:'',
      page:1,
      limit:10,
      totalPages:0,
      sortOptions:[
        {value:'title',name:'По-названию'},
        {value:'body',name:'По-описанию'},
        {value:'id',name:'По-идентификатору'},
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?",
          {params:{
            _page:this.page, 
            _limit: this.limit, 
          }
        });
          this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
        this.posts = response.data;
      } catch (e) {
        alert("Ошибка");
      } finally {
        this.isPostsLoading = false;
      }
    },
    changePage(pageNumber){
      this.page = pageNumber
    },
  },
  computed:{
    sortPosts(){
      return [...this.posts].sort((a, b) => a[this.selectedSort] > b[this.selectedSort] ? 1 : -1)
    },
    sortAndSearchPosts(){
      return this.sortPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    },
  },
  watch:{
    page(){
      this.fetchPosts()
    }
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
* {
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
  padding-bottom: 16px;
}
.row{
  display: flex;
  justify-content: space-between;
  margin: 16px 0;
}
.square {
  width: 100px;
  height: 100px;
  position: relative;
}

.square div {
  position: absolute;
  width: 50px;
  height: 50px;
  background-color: coral;
  animation: flip 2s linear infinite;
  transform-origin: right bottom;
}

.square div:nth-of-type(2) {
  animation-delay: 1s;
  opacity: 0.5;
}

@keyframes flip {
  0% {
    transform: rotateX(0);
  }

  25% {
    transform: rotateY(180deg);
  }

  50% {
    transform: rotateZ(180deg);
  }

  75% {
    transform: rotateX(180deg);
  }

  100% {
    transform: rotateX(0);
  }
}
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}
.pagination-item {
  width: 40px;
  height: 40px;
  background-color: #2c3e50;
  color:#ccc;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: background .3s linear;
}
.pagination-item:hover{
  background-color: #8a8c91;
}
.item-current{
  background-color: #8a8c91;
}
</style>
