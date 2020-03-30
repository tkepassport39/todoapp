<template>
    <div>

        <!-- for each todo send info to todoItem component -->
        <div v-bind:key="todo.id" v-for="todo in todoslist">
            <!-- We are emitting back to app.vue what was emitted from todoItem.vue -->
            <TodoItem v-bind:todoPerItem="todo" v-on:del-todo="$emit('del-todo', todo.id)" />

        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
    // component name
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todoslist"]
}
</script>

<style scoped>

</style>