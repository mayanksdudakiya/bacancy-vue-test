<template>
    <div class="search-wrapper">
        <h1>Github User Search</h1>
        <input type="text" v-model="username"/>
        <input type="button" value="Search" @click="githubSearch"/>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                username: '',
            }
        },
        methods: {
            githubSearch: function() {
                axios.get('https://api.github.com/search/users?q=' + this.username)
                .then(response => {
                    this.$emit('githubusers', response.data)
                }).catch(error => {
                    console.log(error);
                });
            }
        }
    }
</script>

<style scoped>
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=button] {
  width: 100%;
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=button]:hover {
  background-color: #45a049;
}

div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width:30%;
  margin: 0px auto;
}
</style>