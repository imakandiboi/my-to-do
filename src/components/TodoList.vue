<template>
  <div class="container">
    <input type="text " class="todo-input" placeholder="Enter Today's Task" v-model="newTodo" @keyup.enter="addtodo" />
    <div v-for="(todo, index) in todos" :key="todo.id" class="todo-item">
      <div class="todo-item-left">
        <input type="checkbox" v-model="todo.completed" />
        <div v-if="!todo.editing" @click="editTodo(todo)" class="todo-item-label" :class="{ completed: todo.completed }">{{ todo.title }}</div>
        <input v-else class="todo-item-edit" type="text" v-model="todo.title" @blur="editDone(todo)" @keyup.enter="editDone(todo)" @keyup.esc="editCancel(todo)" v-focus />
      </div>
      <div class="remove-item" @click="removeTodo(index)">
        &times;
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo-list",
  idForTodo: 3,
  BeforeEditCache: "",
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: 1,
          title: "take dog for walk",
          completed: false,
          editing: false,
        },
        {
          id: 2,
          title: "cook dinner",
          completed: false,
          editing: false,
        },
      ],
    };
  },
  directives: {
    focus: {
      inserted: function(el) {
        el.focus();
      },
    },
  },

  methods: {
    addtodo() {
      if (this.newTodo.trim().lenght == 0) {
        return;
      }

      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
      });

      this.newTodo = "";
      this.idForTodo++;
    },
    editTodo(todo) {
      this.BeforeEditCache = todo.title;
      todo.editing = true;
    },
    editDone(todo) {
      if (todo.title.trim() == "") {
        todo.title = this.BeforeEditCache;
      }
      todo.editing = false;
    },
    editCancel(todo) {
      todo.title = this.BeforeEditCache;
      todo.editing = false;
    },

    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style scooped>
.todo-input {
  outline-style: none;
  width: 100%;
  padding: 5px 18px;
  font-size: 18px;
  margin-bottom: 5px;
}
.todo-input:focus {
  outline: 0;
}
.todo-item {
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.container {
  border: 3px solid;
  border-radius: 3px;
  background: cornsilk;
  padding: 10px 20px;
}
.remove-item {
  cursor: pointer;
  margin-left: 14px;
  float: right;
}
.remove-item:hover {
  color: red;
}

.todo-item-left {
  display: flex;
  align-items: center;
}
.todo-item-label {
  padding: 5px 18px;

  margin-left: 12px;
}

.todo-item-edit {
  font-size: 18px;
  color: #2c3e50;
  margin-left: 12px;
  width: 100%;
  padding: 5px 18px;
  border: 1px solid rgb(204, 204, 204);
  border-radius: 3px;
  font-family: "avenir", Arial, Helvetica, sans-serif;
}
.todo-item-edit:focus {
  outline: none;
}
.completed {
  text-decoration: line-through;
  color: red;
}
</style>
