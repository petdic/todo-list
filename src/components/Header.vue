<template>
    <div class="header">
        <h1>Todo List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
        background: #0e1111;        
        padding: 10px;
        color: azure;
    }  

    #nav a {
        font-weight: bold;
        color: azure;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }
</style>

