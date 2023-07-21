<template>
  <button class="myButton">
    <slot></slot>
  </button>
</template>

<script setup>

</script>

<style scoped>
.myButton{
    display: block;
    margin: 1rem auto;
    padding: .5rem 2.5rem;
    border: 0;
    border-radius: 1rem;
    color: white;
    background: #5ABF6E;
    transition: .5s ease all;
}

.myButton:hover {
    background: #3a7d47;
    cursor: pointer;
    transition: .5s ease all;
}
</style>