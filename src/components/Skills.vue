
<script setup>
 import { ref, watch } from 'vue';
const emit = defineEmits(['update-skill'])

 const skills = ref([])

 //add skills
 const addSkill = () => {
    skills.value.push({
        name:'',
    })
 }

 //remove skills
 const removeSkill = (index) => {
    skills.value.splice(index, 1)
 }

 //transfer data to app
 watch(skills, (newVal) => {
  emit('update-skill', newVal);
}, { deep: true });
</script>

<template>
    <h3>Skills</h3>
    <div v-for="(skill, index) in skills" class="form repeat" :key="index">
        <div class="row">
            <label for="">Skill</label>
            <input type="text" placeholder="Skill" v-model="skill.name">
        </div>
        <div>
            <button class="form-btn-remove" @click="removeSkill(index)">Remove</button>
        </div>
        
    </div>
    <div>
        <button class="form-btn-add" @click="addSkill">Add skill</button>
    </div>
    
</template>

<style scoped>
.education{
    margin-bottom: 10px;
    border-bottom: 1px solid gray;
    padding: 20px;
}
</style>
