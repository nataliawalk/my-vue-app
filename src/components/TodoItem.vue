<template>
    <div
    class="item"
    v-bind:class="{completed: item.completed}">
        <h2>{{ item.title }}</h2>
        <button v-if="!item.completed" @click="markItemAsDone">Done</button>
    </div>
</template>

<script>
export default {
    props:['item'],
    methods: {
        markItemAsDone() {
            this.$emit('markItemAsDoneClicked', this.item.id)
        }
    }
}
</script>