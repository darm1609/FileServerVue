<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <table border="1">
      <tbody>
        <tr>
          <td><b>Cliente</b></td>
          <td><b>Canal</b></td>
          <td><b>Modo</b></td>
          <td><b>Active</b></td>
          <td><b>Archivos recibidos</b></td>
          <td><b>Archivos enviados</b></td>
        </tr>
        <tr v-for="todo in todos" :key="todo.ClientName">
          <td>{{todo.ClientName}}</td>
          <td>{{todo.Channel.Nombre}}</td>
          <td>{{todo.Mode}}</td>
          <td>{{todo.Active}}</td>
          <td>{{todo.ReceiveFile}}</td>
          <td>{{todo.SendFile}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'FileServer1',
  props: {
    msg: String
  },
  data() {
    return {
      todos : null
    }
  },
  mounted() {
    this.getTodos()
  },
  methods: {

    getTodos: function() {
      setInterval(() => {
        axios.get('http://localhost:8080/api/FileServer/')
          .then(res => {
            this.todos = res.data
            console.log(res);
          }).catch(err => {
            console.log(err.response);
          });  
      }, 1000);
    }    
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
