<template>
    <div class="add-todo">
        <form v-on:submit="addTodo"> 
            <!-- reason why we are calling a method and not the emit is we will first construct the new todo item, then send it as an event with the new item as the payload -->
            <input type="text" v-model="newItem" name="newItem" placeholder="new item...">
            <!-- v-model is used for two way data bindings -->
            <input type="submit" value="Add" class="btn">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data () {
        return {
            newItem:''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();      
            const newTodo = {                
                title: this.newItem,
                completed: false
            }

            //send up to parent
            this.$emit('add-todo', newTodo);

            this.newItem = ''; 
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
}

input[type="text"] {
    flex: 5;
    padding: 5px;
    text-align: center;
    font-size: 20px;
}

input[type="submit"] {
    flex: 5;
    background: #42b983;
    border: none;
    cursor: pointer;
    text-transform: up;
    font-size: 20px;
}
</style>


