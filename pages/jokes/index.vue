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

  async created () {
    const config = {
      headers: {
        Accept: 'Application/json'
      }
    }

    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config)
    } catch (error) {
      console.log(error);
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
  }
}
</script>

<style>

</style>
