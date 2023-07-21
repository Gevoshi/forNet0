<template>
    <h3 class="header">Create Order</h3>
    <div class="form">
        <div class="formItem">
            <h6 class="formText">Table Name</h6>
            <input 
                type="text"
                v-model="order.tableName"
            >
        </div>
        <div class="formItem">
            <h6 class="formText">Number of Seats</h6>
            <input 
                type="number" 
                min="1"
                v-model="order.numberOfSeats"
            >
        </div>
        <div class="formItem">
            <h6 class="formText">Area</h6>
            <select 
                name="area" 
                id="area"
                v-model="order.area"
            >
                <option disabled value="">Area</option>
                <option value="Indoor">Indoor</option>
                <option value="Outdoor">Outdoor</option>
                <option value="Terrace">Terrace</option>
                <option value="Counter">Counter</option>
            </select>
        </div>
        <div class="formItem">
            <label class="formItem">
                <input 
                    type="checkbox"
                    v-model="order.reservable"
                >
                <h6 class="checkBoxText">Reservable</h6>
            </label>
        </div>
    </div>
    <MyButton
        type="submit"
        @click="createOrder"
    >
        Add Table
    </MyButton>
</template>

<script setup>
import MyButton from "./Ui/MyButton.vue";
import { ref } from 'vue';

const emit = defineEmits(['create']) 

const order = ref({
    tableName: '',
    numberOfSeats: '', 
    area: '', 
    reservable: '', 
    action: '(X)'
})

const createOrder = () => {
    order.id = Date.now();
    if(order.value.reservable){
        order.value.reservable = 'Yes'
    }
    else{
        order.value.reservable = 'No'
    }
    emit("create", {...order.value});
    order.value = {
        tableName: '',
        numberOfSeats: '',
        area: '',
        reservable: '',
    };
};
</script>

<style scoped>
.form{
    display: flex;
    justify-content: center;
    align-items: center;
}

.formItem {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: .7rem;
}

.formText {
    margin-right: .5rem;
}

.checkBoxText{
    margin-left: .3rem;
}
</style>