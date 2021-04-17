<template>
  <div>
    <SearchJokes v-on:search-text="searchText"/>
    <Joke v-for='joke in jokes' :key='joke.id' :id='joke.id' :joke='joke.joke' />
  </div>
</template>

<script>

import axios from 'axios'
import Joke from '../../components/joke'
import SearchJokes from '../../components/Searchjokes'

export default {
  components: {
    Joke,
    SearchJokes
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
      this.jokes = res.data.results
    } catch (error) {
      console.log(error)
    }
  },
  methods: {
    async searchText (text) {
      const config = {
        headers: {
          Accept: 'application/json'
        }
      }

      try {
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config)
        this.jokes = res.data.results
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style>

</style>
