<template>
  <div class="todoListContainer">
    <div class="heading">
      <h2 id="title">To Do List</h2>
      <add-item-form
      v-on:reloadList="getList()"
      />
    </div>
    <list-view
    :items="items"
    v-on:reloadList="getList()"
    /> <!--this is a parameter passing to the listview--> <!-- this parent will hear the reloadList event and the it's gonna call the get list function in which will get all items again (make sense) -->
  </div>
</template>

<script>
import addItemForm from "./addItemForm.vue";
import listView from "./listView.vue";
export default {
  components: {
    addItemForm,
    listView,
  },
  data : function() {
      return {
          items : []
      }
  },
  methods : {
      getList (){
          axios.get('api/items')
          .then(response => {
              this.items = response.data
          })
          .catch(error => {
              console.log(error)
          })
      }
  },
  //when this component created
  created() {
      this.getList()
  }
};
</script>

<style scoped>
.todoListContainer {
  width: 350px;
  margin: auto;
}
.heading {
  background: #e6e6e6;
  padding: 10px;
}
#title {
  text-align: center;
}
</style>

