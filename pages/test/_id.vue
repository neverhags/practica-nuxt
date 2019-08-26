<template>
  <div>
    <div>Testeame este id: {{ $route.params.id }}</div>
    <div class="title">
      {{ articulo.title }}
    </div>
    <div class="username">
      {{ articulo.autor.name }}
    </div>
    <div class="body">
      {{ articulo.body }}
    </div>
    <nuxt-link :to="`/test/`" class="btn">
      Atras
    </nuxt-link>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      /* articulo: '' // se usa con created pero se debe eliminar con async */
    }
  },
  async asyncData ({ idDev, route, store, env, params, query, req, res, redirect, error }) {
    let articulo = {}
    try {
      const resp = await axios.get(`https://jsonplaceholder.typicode.com/posts/${route.params.id}`)
      const user = await axios.get(`https://jsonplaceholder.typicode.com/users/${resp.data.userId}`)
      resp.data.autor = await user.data
      articulo = await resp.data
    } catch (e) { console.log(e.message) }
    return { articulo }
  }
  /* async created () {
     try {
      const res = await axios.get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
      const user = await axios.get(`https://jsonplaceholder.typicode.com/users/${res.data.userId}`)
      res.data.autor = await user.data
      this.articulo = await res.data
    } catch (e) { console.log(e.message) }
  } */
}
</script>
<style>
.title {
  font-weight: 600;
  margin: 3px;
}
.username {
  color: #0066ff;
}
.body {
  padding: 7px;
}
.btn {

}
</style>
