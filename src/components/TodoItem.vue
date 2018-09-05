<template>
    <div class="todoItem">
        <div>{{items.name}}</div>
        <button @click='deleteTodo'>Delete {{items.name}}</button>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['items'],
    inject: ['deleteTodoById'],
    methods: {
        deleteTodo: function() {
            this.deleteTodoById(this.items.id);
        }
    }
}
</script>

<style lang="scss">
    .todoItem {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 5px;
        button {
            margin-left: 5px;
        }
    }
</style>
