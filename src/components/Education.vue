
<script setup>
 import { ref, watch } from 'vue';
 const emit = defineEmits(['update-education'])

 const education = ref([])

 //add education
 const addEducation = () => {
    education.value.push({
        school:'',
        course:'',
        from:'',
        end:''
    })
 }

 //remove education
 const removeEducation = (index) => {
    education.value.splice(index, 1)
 }

 //transfer data to app
 watch(education, (newVal) => {
  emit('update-education', newVal);
}, { deep: true });
</script>

<template>
    <h3>Education</h3>
    
        <div v-for="(edu, index) in education" class="form repeat" :key="index">
            <div class="row">
                <label for="">School</label>
                <input type="text" placeholder="School Name" v-model="edu.school">
            </div>
            <div class="row">
                <label for="">Course</label>
                <input type="text" placeholder="Course" v-model="edu.course">
            </div>
            <div class="row">
                <label for="">Start Date</label>
                <input type="text" placeholder="Month/Year" v-model="edu.from">
            </div>
            <div class="row">
                <label for="">End Date</label>
                <input type="text" placeholder="Month/Year" v-model="edu.end">
            </div>
            <div>
                <button class="form-btn-remove" @click="removeEducation(index)">Remove</button>
            </div>
            
        </div>
   
        <div>   
            <button class="form-btn-add" @click="addEducation">Add Education</button>
        </div>
        
</template>

<style scoped>
.education{
    margin-bottom: 10px;
    border-bottom: 1px solid gray;
    padding: 20px;
}
</style>
