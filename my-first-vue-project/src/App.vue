<template>
  <div id="app">
    <!--<img src="./assets/logo.png">
    <router-view></router-view>-->
    <h1 v-text="title"></h1>
    <input v-model="newItem">
    <ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}"
          v-on:click="toggleFinish(item)">
        {{item.lable}}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data: function () {
      return {
        title: 'this is a todo list',
        items: [{
          lable: 'coding',
          isFinished: true
        }, {
          lable: 'walking',
          isFinished: true
        }],
        newItem: ''
      }
    },
    methods: {
      toggleFinish: function (item) {
        item.isFinished = !item.isFinished
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .finished {
    text-decoration: underline;
  }
</style>
