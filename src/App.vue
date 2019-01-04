<template>
  <div id="app">
    <!-- <router-view/> -->
    <button @click="postData">Click to POST data</button>
  </div>
</template>

<script>
const axios = require('axios')
export default {
  name: 'App',
  methods: {
    postData () {
      // axios.post('https://test-vuejs-f012f.firebaseio.com/data.json', {
      //   firstName: 'Dung',
      //   lastName: 'Nguyen'
      // }).then(function (responsive) {
      //   console.log(responsive)
      // })
      axios.get('https://test-vuejs-f012f.firebaseio.com/data.json').then((response) => {
        for (const key in response.data) {
          console.log(response.data[key])
        }
      })
    }
  }
}
</script>

<style>

</style>
