<template>
    <h1>Single Post</h1>
</template>

<script>
import{mapState} from 'vuex'
export default {
  name: "SinglePost",
  async fetch({store, params, error, $axios}){
  const {data} = await $axios.get(`/posts/${params.id}`);
  store.dispatch('setPost', data);
  },
  computed: {
   ...mapState({
       posts: state => state.post.singlePost
    })
  }  
}
</script>