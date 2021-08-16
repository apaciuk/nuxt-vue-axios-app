<template>
<div class="row">
<div class="card" style="width: 34rem;" v-for="post in posts" :key="post.id" >
  <img class="card-img-top" src="https://picsum.photos/400/300" alt="Card image cap">
  <div class="card-body">
    <h3 class="card-title">User - {{post.title}}</h3>
    <p class="card-text">{{post.body}}</p>
    <a href="#" class="btn btn-primary">View More</a>
  </div>
</div>
</div>
</template>

<script>
import {mapState} from 'vuex';
export default {
  name: "PostList"  ,
  async fetch({ store, $axios, error }) {
    const {data} = await $axios.get('/posts');
    store.dispatch('setPosts', data)
  },
  computed: {
      ...mapState({
       posts: state => state.post.posts
      })
  }
}
</script>