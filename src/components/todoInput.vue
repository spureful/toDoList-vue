<template lang='pug'>
.todo__input-block
    input.todo__input(
    type="text"
    placeholder="todo name"
    v-model="todo.name"
    @keydown.enter="addTodo"
    
    ) 

</template>

<script>
let uniqID = 0;
export default {
    data() {
        return {
         todo: {
         id: 0,
         name: '',
         checked: false
         }
        
        }

    },
    methods: {
        addTodo() {
            uniqID++;
            this.todo.id = uniqID;
            this.$emit('addTodo', {...this.todo});
            this.todo.name = " ";
        }
    }
    

}

</script>

<style lang="scss" scoped>
.todo__input-block {
    width: 95%;
    margin: 0 auto;
    margin-bottom: 30px;
}

.todo__input {
    padding: 5px;
    width: 100%;
    height: 20px;
    border-radius: 5px;
}
</style>