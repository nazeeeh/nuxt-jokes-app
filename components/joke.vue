<template>
    <nuxt-link :to="'jokes/' + id">
        <div class="joke">
        {{joke}}
    </div>
    </nuxt-link>
</template>

<script>
export default {
  name: 'Joke',
  props: ['joke', 'id']
}
</script>

<style>
    .joke{
        margin: 1rem 0;
        border: 1px dotted #ccc;
        padding: 1rem;
    }
</style>
