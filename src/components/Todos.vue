<template>
    <div class="todos">
        <div v-for="todo_item in todo_items" v-bind:key="todo_item.id">
            <TodoItem v-bind:item="todo_item" v-on:delete-item="$emit('delete-item-on-list',todo_item.id)"/>
            <!-- we listen for the delete-item event with v-on:delete-item and we want to send another event with a payload -->
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: {
        todo_items: Array //an array called todo_items has been passed to this prop
    }                     //the prop must have the same name as when we v-bind
                          //defining props as objects will allow every prop to have a specific type of value
                          //props: ['todo_items','example'] props can also be defined this way, this way is an array of strings
}
</script>

<style scoped>
.todos {
    text-align: left;
}
</style>


