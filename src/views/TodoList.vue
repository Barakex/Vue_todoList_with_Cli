<template>
  <div class="todoList">
    <h1>Todo list</h1>
    <div class="todoContainer">
      <div class="form">
        <input type="text" class="inputText" v-model='searchValue' />
        <button v-on:click='createTodo()'>Create todo</button>
      </div>
      <TodoItem v-for='items in todoList' :items='items' :key='items.id'/>
    </div>
  </div>
</template>

<script>
import TodoItem from '../components/TodoItem';
import todoList from '../fakeData/todoList';

export default {
  name: 'TodoList',
  data: function() {
    return {
      todoList: todoList,
      searchValue: null,
    }
  },
  methods: {
    createTodo: function() {
      let newTodoItem = {
        id: this.todoList.length + 1,
        name: this.searchValue,
        comlated: false,
      };
      this.todoList.push(newTodoItem);
    },
    deleteTodoById: function(id) {
      const newArr = this.todoList.filter(item => item.id !== id);
      this.todoList = newArr;
    }
  },
  provide: function() {
    return {
      deleteTodoById: this.deleteTodoById,
    }
  },
  components: {
    TodoItem,
  }
}
</script>

<style lang="scss">
  .todoList {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .form {
      display: flex;
      justify-content: center;
      margin-bottom: 15px;
      button {
        margin-left: 5px;
      }
    }
    .todoContainer {
      width: 20%;
      border: 1px solid grey;
      padding: 20px;
    }
    .inputText {
      padding: 5px 10px;
      border: 1px solid grey;
      border-radius: 3px;
      &:focus {
        outline: none;
      }
    }
  }
</style>
