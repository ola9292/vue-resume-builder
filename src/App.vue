<script setup>
import { ref } from 'vue';
  import About from './components/About.vue';
  import Education from './components/Education.vue';
  import Skills from './components/Skills.vue';
  import Experience from './components/Experience.vue';
  import Preview from './components/Preview.vue';
  const step = ref(1)
  const aboutData = ref({})
  const educationData = ref([])
  const experienceData = ref([])
  const skillData = ref([])

  //about me data
  const handleAboutData = (data) => {
    aboutData.value = data
  }

  //education data
  const handleEducationData = (data) => {
    educationData.value = data;
  }

   //experience data
   const handleExperienceData = (data) => {
    experienceData.value = data;
  }


  //skill data
  const handleSkillData = (data) => {
    skillData.value = data;
  }

  //next function
  const next = () => {
    step.value++
  }
  //previous function
  const prev = () => {
    step.value--
  }
</script>

<template>

  <!-- <h3>Resume Builder</h3>
  <p>preview</p>
  <p>{{ aboutData.name }}</p>
  <p>{{ aboutData.role }}</p>
  <p>{{ aboutData.location }}</p>
  <p>{{ aboutData.phone }}</p>
  <p>{{ aboutData.email }}</p>
  <div v-for="education in educationData">
    <div>
      <p>{{  education.school }}</p>
        <p>{{ education.course }}</p>
      <p><span>{{ education.from }}</span> <span>{{ education.end }}</span></p>
    </div>
  </div>
  <div v-for="skill in skillData">
    <p>{{ skill.name }}</p>
  </div> -->
<div class="main container"> 
  <h1 class="text-center">Resume Builder</h1>
  <div v-show="step == 1">
    <About v-show="step == 1" @update-about="handleAboutData"/>
  </div>
  <div v-show="step == 2">
    <Education v-show="step == 2" @update-education="handleEducationData"/>
  </div>
  <div v-show="step == 3">
    <Experience v-show="step == 3" @update-experience="handleExperienceData"/>
  </div>
  <div v-show="step == 4">
    <Skills v-show="step == 4" @update-skill="handleSkillData"/>
  </div>
  
  <div v-show="step == 5">
    <Preview 
    :about-data="aboutData"
    :education-data="educationData" 
    :experience-data="experienceData"
    :skills-data="skillData"
    />
  </div>

  <div class="flex-row">
    <button class="btn" @click="prev" :disabled="step == 1">Prev</button>
    <button class="btn" @click="next" :disabled="step == 5">Next</button>
  </div>
</div>
  
</template>

<style>
  .main{
    font-family: "Smooch Sans", serif;
    font-style: normal;
  }
 .container{
        overflow-x: auto;
        margin: auto;
        padding: 20px;
        width: 90%;
        max-width: 900px;
        box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    }
    .flex-row{
      margin: 10px 0;
      display: flex;
      gap:10px
    }
    .text-center{
      text-align: center;
    }
    .form{
      display: grid;
      gap:15px
    }
    .form > .row{
      display:flex;
      flex-direction: column;
    }
    .form > .row > input{
      padding:10px
    }
    .form > .row > textarea{
      padding:10px;
      height: 150px;
      resize: none;
    }
    .form > .row > label{
      font-size:16px;
      font-weight: bold;
    }
    .repeat{
      border-bottom: 1px solid #d9d9d9;
      padding:20px 0;
    }
    .btn{
      background: #009e74;
      padding:8px 16px;
      border: none;
      color:#fff;
    }
    .form-btn-remove{
      background: orange;
      padding:8px 16px;
      border: none;
      color:#fff;
    }
    .form-btn-add{
      background: black;
      padding:8px 16px;
      border: none;
      color:#fff;
      margin:10px 0;
    }
    .btn:disabled{
      background-color: gray;
      cursor: not-allowed;
    }
</style>
