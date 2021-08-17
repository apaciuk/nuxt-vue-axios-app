<template>
  <div class="container">
    <el-main>
      <el-card class="box-card" v-for="post in posts" :key="post.id" style="margin-bottom:10px">
         <img class="el-card-img" src="https://picsum.photos/400/300" alt="Card image cap">
        <div slot="header" class="clearfix">
          <span>
            <h3>{{post.title}}</h3>
          </span>
         </div>
        <p style="margin-top:15px">{{post.body}}</p>
      <el-button style="padding: 3px 0; margin-top:15px;" type="text" @click="viewDetails(post.id)">View Details</el-button>
      </el-card>
    </el-main>
  </div>
</template>

<script>
import {mapState} from 'vuex';
export default {
name: 'PostList',
async fetch({store, $axios, error}){
  try{
 const {data} = await $axios.get('/posts');
 store.dispatch('setPosts', data);
  }catch(err){
    error({statusCode: 500, message: 'Oops, something went wrong'})
  }
},
computed: {
  ...mapState({
    posts: state => state.post.posts
  })
},
methods: {
  viewDetails(postId){
    this.$router.push({path: `/post/${postId}/details`})
  }
}
}
</script>

<style>
</style>
