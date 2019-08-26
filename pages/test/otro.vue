<template>
  <div>
    <div v-for="(item,k) in menu" :key="k">
      <nuxt-link :to="'/test/' + item.id">
        {{ item.name }}
      </nuxt-link>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      menu: [
        { id: 1, name: 'Nombre menu 1' },
        { id: 2, name: 'Nombre menu 2' },
        { id: 3, name: 'Nombre menu 3' },
        { id: 4, name: 'Nombre menu 4' }
      ]
    }
  }
}
</script>
