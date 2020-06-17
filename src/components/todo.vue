<template lang='pug'>
div
   
    div.todo
        todo-input(
            @addTodo="addTodo"
            )
        todo-list(
        v-if="todos.length > 0"
        :todos="FilteredTodos"
        @removeTodo="removeTodo"
        @todoChecked="todoChecked"
        @filterTodo="filterTodo"
        @checkAll="checkAll"
        )
     

</template>

<script>
import todoInput from './todoInput';
import todoList from './todoList';
export default {
    data () {
        return {
            todos: [],
            filter: "all"
             
    }
  }, 
  components: {
    todoInput,
    todoList
  },
  computed: {
  FilteredTodos() {
  switch(this.filter) {
  case 'all' :
    return this.todos;
case 'active' :
    return this.todos.filter(item => item.checked == false);
case 'completed' :
    return this.todos.filter(item => item.checked);
  }
  } 
 
  },
  

  methods: {
    addTodo(todoname) {
        this.todos.push(todoname)
    },
        removeTodo(todoID) {
      
            this.todos = this.todos.filter(item => item.id !== todoID);
    }, 
    todoChecked(todo) {
   
    this.todos = this.todos.map(item => (item.id == todo.id ? todo : item));
 
    }, 
    filterTodo(filter) {
        this.filter = filter;
    },
    checkAll(todo) {
    
       for (let item of this.todos) {
           todo.checked === true ? item.checked = true : item.checked = false
       }
    }
  
    
   
      
        
    }
  }

</script>

<style lang="scss" scoped>
.todo {
margin-top: 50px;
background-color: #fff;
padding: 10px;
}
</style>