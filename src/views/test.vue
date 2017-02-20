<template>
  <div class="hello">
    <c-title :text="title"></c-title>
    <p class="welcome">这是一个测试路由</p>
    <div v-html="content"></div>
  </div>
</template>

<script>

  import {mapState} from 'vuex';
  import cTitle from 'components/title';

  export default {
    data () {
      return {
        title: 'This is a test page!',
        content: ''
      }
    },
    methods: {
      async getContent () {
        const response = await fetch('/api/hello');
        this.content = await response.text();
      }
    },
    mounted () {
      this.$store.commit('MESSAGE', '欢迎使用 vue！');
      this.getContent();
    },

    components: {cTitle}
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" rel="stylesheet/scss" scoped>
  h1 {
    color: #42b983;
  }

  .logo {
    width: 100px;
    height: 100px;
    a {
      color: #42b983;
      text-decoration: none;
    }
  }
</style>
