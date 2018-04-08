<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{msg2}}</h2>
  </div>
</template>

<script>
import func from '../public/func.js'
import api from '../public/api.js'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      msg2: ''
    }
  },
  methods: {
    getMsg () {
      func.ajaxGet(api.users.users, res => {
        this.msg = res.data
      })
      func.ajaxGet(api.auth.login, res => {
        this.msg2 = res.data
      })
    }
  },
  mounted () {
    this.getMsg()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
