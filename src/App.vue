<template>
  <div>
    <AddTable
      @create="createOrder"
    />
    <Filter
      @filter="filter"/>
    <list
      :displayedItems="displayedItems"
      @remove="removeOrder"
    />
  </div>
</template>

<script setup>
import AddTable from "./components/AddTable.vue";
import List from "./components/List.vue";
import Filter from "./components/Filter.vue";
import { ref, computed} from 'vue';

const orders =  ref([
  {id:1, tableName: 'Table 1', numberOfSeats: 4, area: 'Indoor', reservable: 'Yes', action: '(X)'},
  {id:2, tableName: 'Table 2', numberOfSeats: 6, area: 'Terrace', reservable: "No", action: '(X)'},
])

const filterValue = ref('');

const removeOrder = (order) => {
  orders.value = orders.value.filter(o => o.id !== order.id)
}

const createOrder = (order) => {
  orders.value.push(order)
}

const filter = (filter) => {
  filterValue.value = filter
}

const displayedItems = computed(() => {
    if (filterValue.value === 'Reservable') {
        return orders.value.filter((order) => order.reservable === 'Yes');
    } 
    else {
        return orders.value;
    }
    });
</script>

<style>

*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
</style>
