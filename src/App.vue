<template>
  <div id="app">
    <div>
      <p v-for="item in list">
        Line:
        <span v-text="item"></span>
      </p>
      <infinite-loading @infinite="infiniteHandler"></infinite-loading>
    </div>
  </div>
</template>

<script>
  import InfiniteLoading from 'vue-infinite-loading';
  export default {
    name: 'app',
    data() {
      return {
        list: [],
      };
    },
    methods: {
      infiniteHandler($state) {
        setTimeout(() => {
          const temp = [];
          for (let i = this.list.length + 1; i <= this.list.length + 20; i++) {
            temp.push(i);
          }
          this.list = this.list.concat(temp);
          $state.loaded();
        }, 1000);
      },
    },
    components: {
      InfiniteLoading,
    },
  };
  </script>

  <style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
