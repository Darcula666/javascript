<template>
  <div id="app">
    <!--<img src="./assets/logo.png">
    <router-view></router-view>-->
    <h1 v-text="title"></h1>
    <input v-model="newItem" @keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}"
          v-on:click="toggleFinish(item)">
        {{item.lable}}
      </li>
    </ul>
  </div>
</template>

<script>
  import Store from './store.js'
  export default {
    name: 'app',
    data: function () {
      return {
        title: 'this is a todo list',
        items: Store.fetch(),
        newItem: ''
      }
    },
    watch: {
      items: {
        handler: function (items) {
          Store.save(items)
        },
        deep: true
      }
    },
    methods: {
      toggleFinish: function (item) {
        item.isFinished = !item.isFinished
      },
      addNew: function () {
        this.items.push({
          lable: this.newItem,
          isFinished: false
        })
        Store.save(this.newItem)
        this.newItem = ''
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
