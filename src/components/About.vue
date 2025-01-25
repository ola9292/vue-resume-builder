
<script setup>
 import { ref, watch } from 'vue';
 const emit = defineEmits(['update-about'])

 const about = ref({
    name:'',
    role:'',
    summary:'',
    location:'',
    email:'',
    phone:'',
    url:''

 })

 //transfer data to app
 watch(about, (newVal) => {
  emit('update-about', newVal);
}, { deep: true });
</script>

<template>
<h3>Personal Details</h3>
<div class="form">
    <div class="row">
        <label for="">Name</label>
        <input type="text" placeholder="John Doe" v-model="about.name">
    </div>
    <div class="row">
        <label for="">Role</label>
        <input type="text" placeholder="Software Developer" v-model="about.role">
    </div>
    <div class="row">
        <label for="">location</label>
        <input type="text" placeholder="London" v-model="about.location">
    </div>
    <div class="row">
        <label for="">Email</label>
        <input type="email" placeholder="johndoe@gmail.com" v-model="about.email">
    </div>
    <div class="row">
        <label for="">Phone</label>
        <input type="text" placeholder="12334455" v-model="about.phone">
    </div>
    <div class="row">
        <label for="">Url</label>
        <input type="url" placeholder="www.devwhizz.co.uk" v-model="about.url">
    </div>
    <div class="row">
        <label for="">Summary</label>
        <textarea placeholder="short summary about yourself" v-model="about.summary"></textarea>
    </div>
</div>
</template>

<style scoped>

</style>
