<template>
<div>
      <h1>Search iTunes</h1>
      <br/>

      <form @submit.prevent="submit">
        <input 
          placeholder="Enter Artist Name"
          v-model="search" 
          class="text-center"
          autofocus 
        />

      </form>
</div>
</template>

<script>
export default {
  data: () => ({
    search: ''
  }),
  methods: {
    submit() {
      this.$router.push(`/results/${this.search}`)
    }
  }
}
</script>

<style scoped>

</style>