<template>
    <div>
        <div v-bind:key="eachTodo.id" v-for="eachTodo in todosProp">
            <!-- <h3>{{ eachTodo.title }}</h3> -->
            <TodoItem v-bind:eachTodoItem="eachTodo" v-on:delete-todo="$emit('delete-todo', eachTodo.id)" />
        </div>
    </div>
</template>


<script>
import TodoItem from './TodoItem.vue';

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todosProp"]
}
</script>


<style lang="scss" scoped>

</style>