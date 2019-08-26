<template>
  <div>Testeame este id: {{ $route.params.id }}</div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      articulo: ''
    }
  },
  async created () {
    const res = await axios.get(`https://jsonplaceholder.typicode.com/posts/${$this.params.id}`)
    console.log(res.data)
  }
}
</script>
