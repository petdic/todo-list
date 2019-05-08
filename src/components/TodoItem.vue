<template>
    <div class="todo-item" v-bind:class="{'is-complete':item.completed}"> <!-- the is-complete class will be determined by the truthiness of the data property item.completed -->
        <p>
            <input type="checkbox" class="checkbox" v-on:change="markComplete"/>
            {{item.title}}
            <button v-on:click="$emit('delete-item', item.id)" class="del">x</button>
            <!-- $emit will trigger an event called delete-item and send a payload with it(item.id) -->
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: {
        item: Object
    },
    methods: {
        markComplete() {
            this.item.completed = !this.item.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        padding: 10px;
        background:lightslategray;
        color: azure;
        border-bottom: 3px #ccc solid;      
    }   

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background:crimson;
        color: white;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
        margin-right: 10px;
    }

    .checkbox {
        margin-right: 10px;
        margin-left: 10px;
        cursor: pointer;
    }
</style>


