<template>
<form @submit.prevent="onSubmit">
    <input class="input" type="text" v-model="text" placeholder="Search Jokes...">
    <input class="button" type="submit" value="Submit Jokes">
</form>
</template>

<script>
export default {
  name: 'Searchjokes',
  data () {
    return {
      text: ''
    }
  },
  methods: {
    onSubmit () {
      this.$emit('search-text', this.text)
      this.text = ''
    }
  }
}
</script>

<style>
    form {
        text-align: center;
    }
    .input{
        width: 10rem;
        height: 4vh;
        border-radius: 5px;
        outline: none;
        border: 1px solid #ccc;
    }
    .button {
        padding: 8px;
        border: none;
        color: #fff;
        background: #546288;
        font-weight: bold;
        cursor: pointer;
    }

</style>
