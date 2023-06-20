<template>
  <div class="cv" :class="{ 'dark-mode': isDarkMode }">
    <button class="toggle-button" @click="toggleDarkMode">
      {{ isDarkMode ? 'Light Mode' : 'Dark Mode' }}
    </button>
    <h1>{{ fullName }}</h1>
    <div class="contact">
      <p>Email: {{ email }}</p>
      <p>Phone: {{ phone }}</p>
      <p>Address: {{ address }}</p>
    </div>
    <h2>Education</h2>
    <div class="education">
      <div v-for="educationItem in education" :key="educationItem.id" class="education-item">
        <h3>{{ educationItem.degree }}</h3>
        <p class="institution">{{ educationItem.institution }}</p>
        <p class="year">{{ educationItem.year }}</p>
      </div>
    </div>
    <h2>Experience</h2>
    <div class="experience">
      <div v-for="experienceItem in experience" :key="experienceItem.id" class="experience-item">
        <h3>{{ experienceItem.position }}</h3>
        <p class="company">{{ experienceItem.company }}</p>
        <p class="duration">{{ experienceItem.duration }}</p>
        <ul class="responsibilities">
          <li v-for="responsibility in experienceItem.responsibilities" :key="responsibility.id">
            {{ responsibility }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CV',
  data() {
    return {
      fullName: 'Your Full Name',
      email: 'your.email@example.com',
      phone: '123-456-7890',
      address: 'Your Address, City, Country',
      education: [
        {
          id: 1,
          degree: 'Bachelor of Science',
          institution: 'University of Example',
          year: '2015 - 2019',
        },
        // Add more education items as needed
      ],
      experience: [
        {
          id: 1,
          position: 'Software Developer',
          company: 'Example Company',
          duration: '2019 - Present',
          responsibilities: [
            'Developed web applications using Vue.js',
            'Collaborated with cross-functional teams',
            // Add more responsibilities as needed
          ],
        },
        // Add more experience items as needed
      ],
      isDarkMode: false, // Set this to true for dark mode
    };
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode;
    },
  },
};
</script>

<style scoped>
.cv {
  font-family: Arial, sans-serif;
  color: #333;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.dark-mode {
  background-color: #333;
  color: #fff;
}

.toggle-button {
  position: fixed;
  top: 10px;
  right: 10px;
  padding: 8px 12px;
  background-color: #eee;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

h1 {
  font-size: 24px;
  margin: 20px 0;
}

.contact {
  margin-bottom: 20px;
}

.contact p {
  margin: 5px 0;
}

.education,
.experience {
  margin-bottom: 30px;
}

.education-item h3,
.experience-item h3 {
  font-size: 20px;
  margin-bottom: 10px;
}

.institution,
.company {
  font-weight: bold;
}

.year,
.duration {
  color: #666;
}

.responsibilities {
  margin-top: 10px;
  list-style-type: disc;
  padding-left: 20px;
}

.dark-mode .toggle-button {
  background-color: #555;
  color: #fff;
}

.dark-mode h1,
.dark-mode .company,
.dark-mode .year,
.dark-mode .duration {
  color: #fff;
}

.dark-mode .institution,
.dark-mode .responsibilities li {
  color: #ccc;
}
</style>
