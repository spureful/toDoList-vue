<template lang='pug'>
div
    label.label(:class="{checked: todo.checked}")
        .input-block
            input.checkbox-block(type='checkbox' @change="todoChecked" :checked="todo.checked")
            .checkbox-title {{todo.name}}
        .button
            button(type='button' @click="removeTodo").remove x

        


</template>

<script>


export default {
    props: {
        todo: Object
    },

  components: {
   
  },
  data () {
    return {

    }
  }, 
  
  methods: {
    removeTodo() {
    this.$emit('removeTodo', this.todo.id);
    },
    todoChecked(e) {
      
        const todoItem = {
            ...this.todo,
            checked: e.target.checked
        }
        this.$emit('todoChecked', todoItem);
    
    
    }
  }
}
</script>

<style lang="scss" scoped>


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
//    border: 1px solid black;
//    border-radius: 50%;
border: none;
//    opacity: 0;
   transition: 1s;
   
    &:hover {
      border: 1px solid black;
       
    }
}

.checkbox-block {
    margin-right: 15px;
}
.checked .checkbox-title {
text-decoration: line-through;
}


</style>