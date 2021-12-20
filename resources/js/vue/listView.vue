<template>
  <div>
    <div v-for="(item, index) in items" :key="index">
        <list-item
        :item="item"
        class="item"
        v-on:itemChanged="$emit('reloadList')"
        />
    </div>
    <!-- when this parent hear the itemChanged event , it's gonna fire another event called reloadList -->
  </div>
</template>

<script>
import listItem from './listItem'
export default {
    props : ['items'], //we're recievnig the list of items in a prop called items! (make sense)
    components : {listItem}
}
</script>

<style scoped>
.item {
  background: #e6e6e6;
  padding: 5px;
  margin-top: 5px;
}
</style>
