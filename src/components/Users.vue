<template>
  <div class="container">
    <h3>Users:</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Email</th>
          <th scope="col">Name</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="person in persons" v-bind:key="person.email"> 
          <th scope="row">{{person.email}}</th>
          <td>{{person.name}}</td>
        </tr>
      </tbody>
    </table> 
  </div> 
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Users',
    data() {
      return {
        persons: null,
      };
    },
    created: function() {
      axios
        .get('http://192.168.1.75:5000/persons/')
        .then(res => {
          this.persons = res.data;
        })
    }
  }
</script>

<style>
  h3 {
    margin-bottom: 5%;
  }
</style>