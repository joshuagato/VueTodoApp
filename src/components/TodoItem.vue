<template>
    <div class="todo-item">
        
        <p>
            <section>
                <input type="checkbox" v-on:change="markDone" name="" id="">
                <span  v-bind:class="{'is-done':eachTodoItem.done}">{{ eachTodoItem.title }}</span>
            </section>

            <section v-if="eachTodoItem.done===false"> Added @ {{ date | moment }}</section>
            <section class="is-done" v-if="eachTodoItem.done===true"> Completed @ {{ date | moment }}</section>
            <!-- <section> {{ eachTodoItem.done }}</section> -->

            <button @click="$emit('delete-todo', eachTodoItem.id)" class="delete-item">x</button>
        </p>
        <!-- <p>Ghana</p> -->
    </div>
</template>

<script>
import moment from 'moment';
import { setInterval } from 'timers';

export default {
    name: "TodoItem",
    props: ["eachTodoItem"],
    data() {
        return {
            // myVar: setInterval(this.myTimer, 1000),
            date: new Date()
            // timestamp: moment(this.date).format('lll'),
        }
    },
    methods: {
        markDone() {
            // console.log(123);
            this.eachTodoItem.done = !this.eachTodoItem.done;
            this.date = new Date();
        },
        
        moment: function() {
            return moment();
        }
    },
    filters: {
        moment (date) {
            return moment(date).format('lll');
        }
    }
}
</script>

<style lang="scss" scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;

        p {
            display: flex;
            justify-content: space-between;
        }
    }

    .is-done {
        text-decoration: line-through;
    }

    .delete-item {
        background: #da5757;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        // float: right;
        
        &:hover {
            background-color: #ff0000;
        }
    }
</style>