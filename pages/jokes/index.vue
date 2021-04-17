<template>
  <div>Jokes</div>
</template>

<script>

import axios from 'axios'

export default {
  data () {
    return {
      jokes: []
    }
  },

  head () {
    return {
      title: 'Cracks Tv',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'A place for excellent jokes'
        }
      ]
    }
  },

  async created () {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }

    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config)
      // console.log(res.data.results)
      this.jokes = res.data.results
    } catch (error) {
      console.log(error)
    }
  }
}
</script>

<style>

</style>
