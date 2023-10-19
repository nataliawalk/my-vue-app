<template>
    <div>
        <div>
            <p>new todo: {{ newItem }}</p>
            <input type="text" placeholder="todo" v-model="newItem">
            <button @click="addItem">add</button>
        </div>
        <TodoItem
        v-for="item in items"
        :key="item.id"
        :item="item"
        @markItemAsDoneClicked="markItemAsDone"
        />
    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue'

  export default {
    components: {
        TodoItem
    },
    data() {
      return {
        newItem: '',
        items: [
          { 
            title: 'zrobic zakupy',
            completed: false,
            id: 1
          },
          { 
            title: 'zrobic zakupy1',
            completed: true,
            id: 2
          }
        ]
      }
    },
    methods: {
      addItem() {
        this.items.push({
          title: this.newItem,
          completed: false,
          id: Math.random() 
        })
        this.newItem=''
      },
      markItemAsDone(id) {
        const index = this.items.findIndex(el => el.id === id)
        this.items[index].completed = true
      }
    }
  }
  </script>
  
  <style>
    .item {
      border: 1px solid #cdcdcd;
      margin: 10px;
      padding: 10px;
    }
  
    .completed {
      opacity: 0.5;
    }
  
    .completed h2 {
      text-decoration: line-through;
    }
  </style>