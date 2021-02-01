<template>
    <div class="container">
        <div class="user">
            <h2> Data User dengan nama : {{ user.name }}</h2>
            <ul>
                <li>Username : {{ user.username }}</li>
                <li>Email : {{ user.email }}</li>
            </ul>
            <router-link to="/">Back</router-link>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      user: []
    }
  },
  created () {
    this.getUser()
  },
  methods: {
    getUser () {
      axios.get(`https://jsonplaceholder.typicode.com/users/${this.$route.params.id}`)
        .then((response) => {
          this.user = response.data
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<style scoped>
ul li {
    list-style: none;
}
</style>
