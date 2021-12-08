<template lang='pug'>
.todo__list-block
    .todo__list-content
        input(type="checkbox"
        :checked="isAllTodosChecked"
        @change="checkAll"
        ref="inputAll"
        ).check-all
        h2.title-list TODO LIST
        ul.todo__list
            li.todo__item(v-for="todo in todos")
                todo-list-item(
                :todo="todo"
                @removeTodo="removeTodo"
                @todoChecked="todoChecked"
                )
            
            
    .todo__footer-block
        .todo__footer-content
            .todo__counter {{todos.length}} items left
            .todo__filter
                todo-list-flter(
                @filterTodo="filterTodo"
                )
        


</template>

<script>
import todoListFlter from './todoListFlter';
import todoListItem from './todoListItem';

export default {
    props: {
    todos: Array
    
    },

  components: {
   todoListFlter, todoListItem
  },
  data () {
    return {

    }
  }, 
  computed: {
      isAllTodosChecked() {
        return this.todos.filter(x => x.checked).length === this.todos.length;
      }
  },
  methods: {
  removeTodo(todoID) {
    this.$emit('removeTodo', todoID);
    }, 
    todoChecked(todo) {
       
        this.$emit('todoChecked', todo);
    },
    filterTodo(filter) {
    
    this.$emit('filterTodo', filter);
    }, 
    checkAll() {
      const inputAll = this.$refs.inputAll
        this.$emit('checkAll', inputAll)
    }
  }
}
</script>

<style lang="scss" scoped>
.todo__list {
    font-size: 20px;
    border-bottom: 2px solid #000;
    border-top: 2px solid #000;
}


.todo__item {
    border-bottom: 1px solid  #000;
    padding-top: 15px;
    padding-bottom: 15px;
    &:last-child {
    border-bottom: none;
    }
   
}

.label {
 display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;
   justify-content: space-between;
}

.input-block {
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;
    
}

.todo__footer-block {
    color: #777;
    padding: 10px 15px;
    text-align: center;
    position: relative;
    font-size: 14px;}
    
    .remove {
    font-size: 20px;
    background-color: transparent;
   border: 1px solid black;
   border-radius: 50%;

   opacity: 0;
   transition: 1s;
   
    &:hover {
        opacity: 1;
       
    }
}

.checkbox-block {
    margin-right: 15px;
}

.todo__footer-content {
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;
}



.todo__filter {
margin: 0 auto;
}

.title-list {
display: inline-block;
margin-left: 30%;
}
</style>