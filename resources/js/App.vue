<template>
  <div class="container">
    <div v-for="post in posts" :key="post.id">
        <h3>{{ post.title }}</h3>
        <p>{{ post.content }}</p>
    </div>
  </div>
</template>

<script>
export default {
    name: 'App',

    data() {
        return{

            apiUrl: 'http://127.0.0.1:8000/api/posts',

            posts: null,

        }
    },

    methods: {
        getApi() {
            axios.get(this.apiUrl)
            .then(res => {
                this.posts = res.data;
            })
        }
    },

    mounted() {
        this.getApi();
    }
}
</script>

<style>

</style>
