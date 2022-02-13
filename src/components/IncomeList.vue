<template>
  <div class="title">
    <p>Income List</p>
  </div>
 <div class="income-list">
    <Items @remove-item="removeItem" v-for="data in state.sortedIncome" :key="data.id" :income="data"/>
 </div>
</template>

<script>
import Items from './Items.vue'

export default {
    emits: ["remove-item"],
    components: {Items},
    props: {
        state: Object
    },

    setup(props,{emit}) {
        function removeItem(id){
            emit("remove-Item", id)
        }

        return {
            removeItem
        }
    }
}
</script>
