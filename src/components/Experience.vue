
<script setup>
 import { ref, watch } from 'vue';
 const emit = defineEmits(['update-experience'])

 const experience = ref([])

 //add skills
 const addExperience = () => {
    experience.value.push({
        employer:'',
        position:'',
        start:'',
        end:'',
        description:''
    })
 }

 //remove skills
 const removeExperience = (index) => {
    experience.value.splice(index, 1)
 }

 //transfer data to app
 watch(experience, (newVal) => {
  emit('update-experience', newVal);
}, { deep: true });
</script>

<template>
    <h3>Experience</h3>
    <div v-for="(ex, index) in experience" class="form repeat" :key="index">
        <div class="row">
            <label for="">Employer</label>
            <input type="text" placeholder="Employer" v-model="ex.employer">
        </div>
        <div class="row">
            <label for="">Position</label>
            <input type="text" placeholder="Position" v-model="ex.position">
        </div>

        <div class="row">
            <label for="">Start Date</label>
            <input type="text" placeholder="mm/yy" v-model="ex.start">
        </div>

        <div class="row">
            <label for="">End Date</label>
            <input type="text" placeholder="mm/yy" v-model="ex.end">
        </div>

        <div class="row">
            <label for="">Description</label>
            <textarea v-model="ex.description"/>
        </div>

        <div>
            <button class="form-btn-remove" @click="removeExperience(index)">Remove</button>
        </div>
        
    </div>
    <div>
        <button class="form-btn-add" @click="addExperience">Add Experience</button>
    </div>
    
</template>

<style scoped>
.education{
    margin-bottom: 10px;
    border-bottom: 1px solid gray;
    padding: 20px;
}
</style>
