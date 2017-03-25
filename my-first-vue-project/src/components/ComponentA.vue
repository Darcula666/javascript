<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="onClickMe">Click!</button>
  </div>
</template>
<script>
  export default {
    data: function () {
      return {
        msg: 'hello from componet a !'
      }
    },
    props: ['msgfromFather'],
    methods: {
      onClickMe: function () {
        console.log(this.msgfromFather)
      }
    }
  }
</script>
