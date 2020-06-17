<template lang='pug'>
.filter
    button(
    v-for="filter in filters"
    :class="{active: currentFilter == filter}"
    @click="filterTodo(filter)"
    type="button") {{filter}}
        
</template>


<script>
export default {
    data () {
        return {
            filters: ['all', 'active', 'completed'],
            currentFilter: 'all'
             
    }
  },
  

  methods: {
    filterTodo(filter) {
        this.currentFilter = filter
        this.$emit('filterTodo', filter);
    }
  }
}

</script>
<style lang="scss" scoped>
button {
    margin-right: 20px;
    border: none;
    background: transparent;
    font-weight: 300;
    cursor: pointer;
    border: 1px solid transparent;
    border-radius: 3px;
    
    &.active {
       border: 1px solid grey; 
       background-color: rgba(grey, 0.2);
    }
    
    &:last-child {
    margin-right: 0;
    }
}


</style>