<template>
  <div class="filter">
    <h3 class="filterHeader">Tables</h3>
    <label class="filterItem">
        <input 
            class="filterInput"
            name="filter"
            type="radio"
            value="All"
            v-model="filter"
        >
        <span class="radio-checkmark"></span>
        <p>All</p>
    </label>
    <label class="filterItem">
        <input
            class="filterInput"
            name="filter" 
            type="radio"
            value="Reservable"
            v-model="filter"
        >
        <span class="radio-checkmark"></span>
        <p>Reservable</p>
    </label>
  </div>
</template>

<script setup>
import { ref, watch, defineProps, defineEmits } from 'vue';

defineProps({
    Orders: Array
})

const emit = defineEmits(['filter'])

const filter = ref('All')

watch(filter, (newValue) => {
        emit('filter', newValue)
    }
) 
</script>

<style>
.filter{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1.4rem;
}

.filterItem {
    display: flex;
    justify-content: center;
    align-items: center;
}

.filterItem input{
    position: absolute;
    opacity: 0;
    cursor: pointer;
}


.filterHeader {
    margin-right: 1rem;
}

.radio-checkmark {
  position: relative;
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  border: 2px solid #E2E3E3;
  margin-right: .6rem;
}

input:checked + .radio-checkmark {
  background-color: #5ABF6E;
}
</style>