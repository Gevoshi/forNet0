<template>
    <table>
        <tr class="row">
            <td class="block">{{ order.tableName }}</td>
            <td class="block">{{ order.numberOfSeats }}</td>
            <td class="block">{{ order.area }}</td>
            <td class="block">{{ order.reservable }}</td>
            <td class="block delete" @click="emit('remove', order)">(X)</td>
        </tr>
    </table>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps({
    order: Object
})

const emit = defineEmits(['remove']) 
</script>

<style>
.delete{
    cursor: pointer;
}
</style>