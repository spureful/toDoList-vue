<template lang='pug'>
    .container
        todo
  
</template>

<script>
import todo from './components/todo'
export default {
  name: 'app',
  components: {
    todo
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss">
body {
font-family: Helvetica, sans-serif;
line-height: 1.42;
background: #f5f5f5;

}

ul {
margin: 0;
padding: 0;
}

li {
    list-style: none;
}

.container {
    width: 600px;
    margin: 0 auto;
}

</style>
