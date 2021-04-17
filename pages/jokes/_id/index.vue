<template>
  <div>
    <nuxt-link to="/jokes"> Back to jokes
    </nuxt-link>
      <h4>{{ joke }}</h4>
      <hr />
      <small>Joke:ID {{ $route.params.id }}</small>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  data () {
    return {
      joke: {}
    }
  },

  head () {
    return {
      title: this.joke,
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
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config)
      this.joke = res.data.joke
    } catch (error) {
      console.log(error)
    }
  }
}
</script>

<style>

</style>
