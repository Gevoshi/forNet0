<template>
    <h3 class="header">Create Order</h3>
    <div class="form">
        <div class="formItem">
            <h5 class="formText">Table Name</h5>
            <input 
                type="text"
                v-model="order.tableName"
                @keyup.enter="createOrder" 
                class="inputText" 
            >
        </div>
        <div class="formItem">
            <h5 class="formText">Number of Seats</h5>
            <input 
                type="number" 
                min="1"
                v-model="order.numberOfSeats"
                @keyup.enter="createOrder" 
                class="inputNumber" 
            >
        </div>
        <div class="formItem">
            <h5 class="formText">Area</h5>
            <select 
                name="area" 
                id="area"
                v-model="order.area"
                @keydown.enter="createOrder"
                class="selectArea" 
            >
                <option disabled value="" class="defaultOption">Area</option>
                <option value="Indoor" class="option">Indoor</option>
                <option value="Outdoor" class="option">Outdoor</option>
                <option value="Terrace" class="option">Terrace</option>
                <option value="Counter" class="option">Counter</option>
            </select>
        </div>
        <div class="formItem">
            <label class="formItem">
                <input 
                    type="checkbox"
                    v-model="order.reservable"
                    @keyup.enter="createOrder"
                    class="checkboxInput" 
                >
                <span class="checkmark"></span>
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
    numberOfSeats: 0, 
    area: '', 
    reservable: false, 
    action: '(X)'
})

const createOrder = () => {
    order.value.id = Date.now();
    if(order.value.reservable){
        order.value.reservable = 'Yes'
    }
    else{
        order.value.reservable = 'No'
    }
    emit("create", {...order.value});
    order.value = {
        tableName: '',
        numberOfSeats: 0,
        area: '',
        reservable: false,
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
    color: #757575;
}

.defaultOption{
    color: rgb(255, 255, 255);
}

.inputText {
    border-radius: 10px;
    border: 2px solid #D8D9D9;
    padding: 5px;
}

.inputNumber{
    border-radius: 10px;
    border: 2px solid #D8D9D9;
    padding: 5px;
    width: 40px;
    height: 30px;
}

.formItem .selectArea {
    border-radius: 10px;
    border: 2px solid #D8D9D9;
    padding: 5px;
    height: 30px;
    padding-right: 20px;
}

.checkboxInput{
    position: absolute;
    opacity: 0;
    cursor: pointer;
}
.checkmark {
  position: relative;
  display: inline-block;
  width: 15px;
  height: 15px;
  border: 2px solid #D8D9D9;
  border-radius: 2px;
  background-color: #fff;
}

.checkboxInput:checked + .checkmark {
  background: #5ABF6E;; 
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.checkboxInput:checked + .checkmark:after {
  display: block;
  left: 3px;
  width: 3px;
  height: 8px;
  border: solid white;
  border-width: 0 3px 3px 0;
  transform: rotate(45deg);
}
</style> 