<template>
  <div>
    <Joke v-for='joke in jokes' :key='joke.id' :id='joke.id' :joke='joke.joke' />
  </div>
</template>

<script>

import axios from 'axios'
import Joke from '../../components/joke'

export default {
  components: {
    Joke
  },

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
