<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";

export default {
  components: {
    PostList, PostForm
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'Javascript', body: 'Описание поста'},
        {id: 2, title: 'Javascript 2', body: 'Описание поста 2'},
        {id: 3, title: 'Javascript 3', body: 'Описание поста 3'},
        {id: 4, title: 'Javascript 4', body: 'Описание поста 4'},
      ],
      dialogVisible: false,
      modificatorValue: ''
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    }
  }
}
</script>

<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <my-button @click="showDialog" style="margin: 15px 0;">
      Создать пост
    </my-button>
    <my-dialog
        v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </my-dialog>
    <post-list
        v-bind:posts="posts"
        @remove="removePost"
    />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
  width: 1000px;
  margin: 0 auto;
}

</style>
