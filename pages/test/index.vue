<template>
  <div>
    <div v-for="(item,index) in articulos" :key="index" class="content">
      <nuxt-link :to="`/test/${item.id}`">
        <div class="title">
          {{ item.title }}
        </div>
        <div>
          {{ item.body }}
        </div>
      </nuxt-link>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      articulos: []
    }
  },
  async created () {
    try {
      const res = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
      console.log(res.data)
      this.articulos = res.data
    } catch (e) {
      console.log(e.message)
    }
  }
}
</script>
<style lang="css">
.content {
  padding:15px;
}
.title {
  margin: 5px;
  font-weight: 600;
}
</style>
