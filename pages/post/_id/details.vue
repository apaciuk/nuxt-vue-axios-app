<template>
  <div class="container">
    <el-main>
      <el-card class="box-card">
      <img class="el-card-img" src="https://picsum.photos/400/300" alt="Card image cap">
        <div slot="header" class="clearfix">
          <span>
            <h3>{{post.title}}</h3>
          </span>
         </div>
        <p style="margin-top:15px">{{post.body}}</p>
             <el-button style="padding: 3px 0; margin-top:15px;" type="text" @click="editPost(post.id)">Edit</el-button>
          <el-button style="padding: 3px 0; margin-top:15px;" type="text" @click="deletePost(post)">Delete</el-button>
      </el-card>
    </el-main>
  </div>

</template>

<script>
import {mapState} from 'vuex';
export default {
name: 'PostDetails',
async fetch({store, params, error, $axios}){
  const {data} = await $axios.get(`/posts/${params.id}`);
  store.dispatch('setPost', data);
},
computed: {
  ...mapState({
    post : state => state.post.singlePost
  })
},
methods: {
  editPost(postId){
    this.$router.push({path: `/post/${postId}/edit`})
  },
  deletePost(post){
    this.$store.dispatch('deletePost', post);
    this.$router.push({path: `/post/list`})
  }
}
}
</script>

<style>
</style>
