<template>
  <section class="container">
    <div>
 
    <img src="header.jpg" style="margin:30px; text-align:center;" />
  
      {{posts}}
    </div>
  </section>
</template>

<script>
import {mapState} from 'vuex';
export default {
  computed: {
    ...mapState({
      posts: state => state.post.posts
    })
  }
}
</script>

<style>
.container {
	min-height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
	text-align: center;
}

.title {
	font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
		'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
	display: block;
	font-weight: 300;
	font-size: 100px;
	color: #35495e;
	letter-spacing: 1px;
}

.subtitle {
	font-weight: 300;
	font-size: 42px;
	color: #526488;
	word-spacing: 5px;
	padding-bottom: 15px;
}

.links {
	padding-top: 15px;
}
</style>
