<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn-submit">
        </form>
        <p></p>
        <Bind v-bind:bindTitle="title" />
    </div>
</template>


<script>
import uuid from 'uuid';
import Bind from './layouts/Bind.vue';

export default {
    name: "AddTodo",
    components: {
        Bind
    },
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                done: false
            }
            // Send up to parent
            console.log(this.title);
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>


<style lang="scss" scoped>
    form {
        display: flex;
    }

    input {
        
        &[type="text"] {
            flex: 10;
            padding: 5px;
        }

        &[type="submit"] {
            flex: 2;
        }
    }

    .btn-submit {
        display: inline-block;
        border: none;
        background: #555;
        color: #fff;
        padding: 7px 40px;
        cursor: pointer;

        &:hover {
            background: #666;
        }
    }

</style>