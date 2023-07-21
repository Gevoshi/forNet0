<template>
    <h4 class="header">Table List</h4>
    <div class="tableMain" 
        v-if="displayedItems.length > 0"
    >
        <table>
            <tr class="row">
                <td class="block">Table Name</td>
                <td class="block">Number of Seats</td>
                <td class="block">Area</td>
                <td class="block">Reservable</td>
                <td class="block">Actions</td>
            </tr>
            <ListItem
                v-for="order in displayedItems"
                :key="order.id"
                :order="order"
                @remove="emit('remove', order)"
            />
        </table>
    </div>

    <h3 v-else class="emptyText">Empty</h3>
</template>

<script setup>
import ListItem from './ListItem.vue';
import { defineProps } from 'vue';
defineProps({
    displayedItems: Array
})

const emit = defineEmits(['remove']) 

</script>

<style>

.tableMain {
    display: flex;
    justify-content: center;
    align-items: center;
}

.row{
    display: flex;
    justify-content: center;
    align-items: center;
}
.block{
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    border: 1px solid hsl(0, 0%, 0%);
    width: 9rem;
    height: 2rem;
    font-weight: 600;
}

.header,
.emptyText{
    text-align: center;
    margin: 2rem 0;
}

</style>