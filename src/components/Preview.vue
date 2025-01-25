
<script setup>
 import { defineProps } from 'vue';
 import html2pdf from 'html2pdf.js';
 const props = defineProps({
  aboutData: {
    type: Object,
    required: true,
    default: () => ({})
  },
  educationData: {
    type: Array,
    required: true,
    default: () => []
  },
  experienceData: {
    type: Array,
    required: true,
    default: () => []
  },
  skillsData: {
    type: Array,
    required: true,
    default: () => []
  }
})

// Download PDF
const downloadPDF = () => {
  const element = document.getElementById('resume-preview');
  const options = {
    margin:[1, 1, 1.5, 1],
    filename: 'resume.pdf',
    image: { type: 'jpeg', quality: 0.98 },
    html2canvas: { scale: 2, windowWidth: 1024, windowHeight: 600 },
    jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' },
  };
  html2pdf().from(element).set(options).save();
};

</script>

<template>
    <div id="resume-preview">
        <div class="about">
            <h1 class="name text-center" style="margin-bottom: 10px; color:green">{{ aboutData.name }}</h1>
            <div class="details">
                <p class="detail capitalize">{{ aboutData.role }}</p>
                <p class="detail">{{ aboutData.email }}</p>
                <p class="detail">{{ aboutData.phone }}</p>
                <p class="detail">{{ aboutData.url }}</p>
            </div>
            <p class="">{{ aboutData.summary }}</p>
        </div>
        <div class="skills" v-if="skillsData.length > 0">
            <h2>Skills</h2>
            <ul>
                <li v-for="(skill, index) in skillsData" :key="index" class="skill">
                    {{ skill.name }},
                </li>
            </ul>
        </div>
        <div class="experience" v-if="experienceData.length > 0">
            <h2>Experience</h2>
            <div v-for="(experience, index) in experienceData" :key="index">
                <h3><bold>{{ experience.position }}</bold></h3>
                <div class="employer">
                    <p>{{ experience.employer }}</p>
                    <div>
                        <span>{{ experience.start }}</span> -
                        <span>{{ experience.end }}</span>
                    </div>
                </div>
                <ul>
                    <li v-for="(line, index) in experience.description.split('\n')" :key="index">
                    {{ line }}
                    </li>
                </ul>
            </div>
        </div>
        <div class="experience" v-if="educationData.length > 0">
            <h2>Education</h2>
            <div v-for="(education, index) in educationData" :key="index">
                <h3><bold>{{ education.school }}</bold></h3>
                <div class="employer">
                    <p>{{ education.course }}</p>
                    <div>
                        <span>{{ education.from }}</span> -
                        <span>{{ education.end }}</span>
                    </div>
                </div>
            </div>
        </div>
        
    </div>
    <button class="btn" @click="downloadPDF">Download PDF</button>
</template>

<style scoped>
    .about > h1{
        margin:0;
    }
    .about > .details{
        display:flex;
        justify-content: center;
        gap:10px
    }
    .details > .detail{
        margin: 0;
        padding-right:5px;
        border-right: 1px solid gray;
    }
    .skills > ul {
       display:flex;
       gap:5px;
       padding:0;
    }
    .skills > ul > li, .experience > ul > li{
        list-style-type: none;
    }
    .capitalize{
        text-transform: capitalize;
    }
    .experience{
        margin-bottom: 20px;
    }
    .experience > .employer{
        display: flex;
        justify-content: space-between;
    }
    #resume-preview {
        font-family: "Smooch Sans", serif;
        font-style: normal;
        margin-bottom: 30px;
  }

</style>
