<script setup>
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue'


const darkMode = ref(false)
const toggleTheme = () => {
  darkMode.value = !darkMode.value
  document.body.classList.toggle('dark-mode')
}

//section 
const isExpanded = ref(false)
const toggleExpand = () => {
  isExpanded.value = !isExpanded.value
}


const socialLinks = [
  { name: 'GitHub', icon: '💻', url: 'https://github.com/Nebiyou-x?tab=repositories', hover: 'View my code ' },
  { name: 'LeetCode', icon: '🧩', url: 'https://leetcode.com/u/nebiyou23/', hover: 'Check my problem-solving skills' },
  { name: 'LinkedIn', icon: '💼', url: 'https://linkedin.com/in/', hover: 'contact me for work opportunities' },
  { name: 'Twitter', icon: '🐦', url: 'https://x.com/Nebiyou23', hover: 'Follow me for tech updates' }
]


const skills = [
  { name: 'HTML', level: 90, icon: '🌐' },
  { name: 'CSS', level: 85, icon: '🎨' },
  { name: 'JavaScript', level: 88, icon: '⚡' },
  { name: 'Vue.js', level: 66, icon: '💚' },
  { name: 'React.js', level: 60, icon: '🚀' },
  { name: 'Git', level: 40, icon: '📚' }
]


const projects = [
  {
    title: 'Project 1',
    description: 'A web application built with Vue.js',
    image: 'https://i.postimg.cc/R0v0RXfY/Dormitory-image.png',
    link: '#'
  },
  {
    title: 'Project 2',
    description: 'Currency info',
    image: 'https://i.postimg.cc/bJWD31q2/screencapture-ethioexchange-pro-et-2025-01-29-00-02-59.png',
    link: 'https://ethioexchange.pro.et/'
  },
  {
    title: 'Project 3',
    description: 'An e-commerce platform',
    image: 'https://i.postimg.cc/CLyn8Cv3/screencapture-nebiyou-x-github-io-kedisho-github-io-2025-01-29-00-05-55.png',
    link: 'https://nebiyou-x.github.io/kedisho.github.io/'
  }
]


const experiences = [
  {
    company: 'Ayaan Solutions Inc.',
    position: 'Digital Marketer',
    period: '2024 - Present',
    description: 'promoting a companys products or services online using various digital channels like social media, search engines, email marketing, and websites'
  },
  {
    company: 'Dan Digital Innovations',
    position: 'Web Developer',
    period: '2024-Present',
    description: 'Developed responsive websites and web applications using Vue.js and other modern frameworks.'
  },
  {
    company: 'StartUp Hub',
    position: 'Junior Developer',
    period: '2024-Present',
    description: 'Started career working on various web development projects and learning modern technologies.'
  }
]


const formData = ref({
  name: '',
  email: '',
  message: ''
})

const submitForm = () => {
  
  console.log('Form submitted:', formData.value)
  
  formData.value = {
    name: '',
    email: '',
    message: ''
  }
}
</script>

<template>
  <div class="portfolio" :class="{ 'dark-mode': darkMode }">
    
    <header>
      <div class="theme-toggle">
        <button @click="toggleTheme" class="theme-btn">
          {{ darkMode ? '☀️' : '🌙' }}
        </button>
      </div>
      <div class="profile-container">
        <img 
          src="https://i.postimg.cc/qqqhGjfr/IMG-5536.jpg" 
          alt="Profile" 
          class="profile-image"
        />
        <h1 class="animate-title">Nebiyou Tsegaye</h1>
        <p class="animate-subtitle">Web Developer</p>
        
        
        <div class="social-links">
          <a 
            v-for="social in socialLinks" 
            :key="social.name"
            :href="social.url"
            :title="social.hover"
            target="_blank"
            rel="noopener noreferrer"
            class="social-link"
          >
            <span class="social-icon">{{ social.icon }}</span>
            <span class="social-name">{{ social.name }}</span>
          </a>
        </div>
      </div>
    </header>
    
    <main>
      <!-- About Section -->
      <section class="about">
        <h2>About Me</h2>
        <div class="about-content" :class="{ 'expanded': isExpanded }">
          
          <p>
            Hi! I'm a passionate Front end web developer with a focus on creating clean and user-friendly applications.
            I enjoy solving problems and learning new technologies.
          </p>
          <p v-if="isExpanded">
            With over 2 years of experience in web development, I've worked on various projects
            ranging from small business websites to large-scale applications. I'm particularly
            interested in creating intuitive user interfaces and optimizing application performance.
          </p>
          <button @click="toggleExpand" class="expand-btn">
            {{ isExpanded ? 'Read Less' : 'Read More' }}
          </button>
        </div>
      </section>

      
      <section class="experience">
        <h2>Experience</h2>
        <div class="timeline">
          <div 
            v-for="(exp, index) in experiences" 
            :key="index"
            class="timeline-item"
            :class="{ 'fade-in': true }"
            :style="{ animationDelay: `${index * 0.2}s` }"
          >
            <div class="timeline-content">
              <h3>{{ exp.position }}</h3>
              <h4>{{ exp.company }}</h4>
              <p class="period">{{ exp.period }}</p>
              <p class="description">{{ exp.description }}</p>
            </div>
          </div>
        </div>
      </section>

      
      <section class="skills">
        <h2>Skills</h2>
        <div class="skills-grid">
          <div 
            v-for="skill in skills" 
            :key="skill.name" 
            class="skill-card"
          >
            <div class="skill-icon">{{ skill.icon }}</div>
            <h3>{{ skill.name }}</h3>
            <div class="skill-bar-container">
              <div 
                class="skill-bar" 
                :style="{ width: skill.level + '%' }"
              ></div>
            </div>
            <span class="skill-level">{{ skill.level }}%</span>
          </div>
        </div>
      </section>

      
      <section class="projects">
        <h2>Projects</h2>
        <div class="projects-grid">
          <div 
            v-for="project in projects" 
            :key="project.title" 
            class="project-card"
          >
            <div class="project-image-container">
              <img :src="project.image" :alt="project.title" class="project-image">
              <div class="project-overlay">
                <a :href="project.link" class="view-project">View Project</a>
              </div>
            </div>
            <div class="project-info">
              <h3>{{ project.title }}</h3>
              <p>{{ project.description }}</p>
            </div>
          </div>
        </div>
      </section>

     
      <section class="contact">
        <h2>Contact Me</h2>
        <div class="contact-container">
          <div class="contact-info">
            <div class="contact-item">
              <span class="contact-icon">📧</span>
              <a href="mailto:john.doe@example.com">Nebiyoutsegaye99@gmail.com</a>
            </div>
            <div class="contact-item">
              <span class="contact-icon">📱</span>
              <a href="tel:+1234567890">+251 955 330 626</a>
            </div>
            <div class="contact-item">
              <span class="contact-icon">📍</span>
              <span>Addis Ababa, ET</span>
            </div>
          </div>
          <form @submit.prevent="submitForm" class="contact-form">
            <div class="form-group">
              <label for="name">Name</label>
              <input 
                type="text" 
                id="name" 
                v-model="formData.name" 
                required
              >
            </div>
            <div class="form-group">
              <label for="email">Email</label>
              <input 
                type="email" 
                id="email" 
                v-model="formData.email" 
                required
              >
            </div>
            <div class="form-group">
              <label for="message">Message</label>
              <textarea 
                id="message" 
                v-model="formData.message" 
                required
              ></textarea>
            </div>
            <button type="submit" class="submit-btn">Send Message</button>
          </form>
        </div>
      </section>
    </main>
  </div>

</template>

<style scoped>
.portfolio {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  transition: all 0.3s ease;
}

.dark-mode {
  background-color: #1a1a1a;
  color: #ffffff;
}


header {
  text-align: center;
  margin-bottom: 3rem;
  position: relative;
}

.theme-toggle {
  position: absolute;
  top: 1rem;
  right: 1rem;
}

.theme-btn {
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 50%;
  transition: transform 0.3s ease;
}

.theme-btn:hover {
  transform: rotate(360deg);
}

.profile-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.profile-image {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid #646cff;
  transition: transform 0.3s ease;
}

.profile-image:hover {
  transform: scale(1.05);
}

/* About Section Styles */
.about {
  margin-bottom: 3rem;
}

.about-content {
  position: relative;
  transition: all 0.3s ease;
}

.about-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 1rem;
  transition: transform 0.3s ease;
}

.about-image:hover {
  transform: scale(1.02);
}

.expand-btn {
  background-color: #646cff;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 1rem;
  transition: background-color 0.3s ease;
}

.expand-btn:hover {
  background-color: #4b50bf;
}

/* Skills Section Styles */
.skills {
  margin-bottom: 3rem;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
}

.skill-card {
  background-color: #f1f1f1;
  padding: 1.5rem;
  border-radius: 8px;
  transition: transform 0.3s ease;
}

.skill-card:hover {
  transform: translateY(-5px);
}

.skill-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.skill-bar-container {
  width: 100%;
  height: 8px;
  background-color: #ddd;
  border-radius: 4px;
  overflow: hidden;
  margin: 0.5rem 0;
}

.skill-bar {
  height: 100%;
  background-color: #646cff;
  border-radius: 4px;
  transition: width 1s ease-out;
}

.skill-level {
  font-size: 0.9rem;
  color: #666;
}

/* Projects Section Styles */
.projects {
  margin-bottom: 3rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.project-card {
  background-color: #f1f1f1;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
}

.project-image-container {
  position: relative;
  overflow: hidden;
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(100, 108, 255, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-image-container:hover .project-overlay {
  opacity: 1;
}

.project-image-container:hover .project-image {
  transform: scale(1.1);
}

.view-project {
  color: white;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border: 2px solid white;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.view-project:hover {
  background-color: white;
  color: #646cff;
}

.project-info {
  padding: 1.5rem;
}

.project-info h3 {
  margin-bottom: 0.5rem;
}

/* Experience Section Styles */
.experience {
  margin-bottom: 3rem;
}

.timeline {
  padding: 2rem 0;
}

.timeline-item {
  padding: 1.5rem;
  background-color: #f1f1f1;
  border-radius: 8px;
  margin-bottom: 1.5rem;
  position: relative;
  transition: transform 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.timeline-item:hover {
  transform: translateX(10px);
}

.timeline-content h3 {
  margin: 0;
  color: #646cff;
}

.timeline-content h4 {
  margin: 0.5rem 0;
  color: #666;
}

.timeline-content .period {
  font-size: 0.9rem;
  color: #888;
  margin-bottom: 0.5rem;
}

.timeline-content .description {
  line-height: 1.6;
}
/* Contact Section Styles */
.contact {
  margin-bottom: 3rem;
}

.contact-container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 2rem;
}

.contact-info {
  padding: 1.5rem;
  background-color: #f1f1f1;
  border-radius: 8px;
}

.contact-item {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.contact-icon {
  font-size: 1.5rem;
  margin-right: 1rem;
}

.contact-item a {
  color: #646cff;
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-item a:hover {
  color: #4b50bf;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-family: inherit;
  transition: border-color 0.3s ease;
}

.form-group textarea {
  min-height: 150px;
  resize: vertical;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #646cff;
}

.submit-btn {
  background-color: #646cff;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  font-weight: 500;
  transition: background-color 0.3s ease;
}

.submit-btn:hover {
  background-color: #4b50bf;
}

/* Social Links Styles */
.social-links {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background-color: #f1f1f1;
  border-radius: 2rem;
  text-decoration: none;
  color: inherit;
  transition: all 0.3s ease;
}

.social-link:hover {
  transform: translateY(-2px);
  background-color: #646cff;
  color: white;
}

.social-icon {
  font-size: 1.2rem;
}

.social-name {
  font-size: 0.9rem;
  font-weight: 500;
}

/* Dark mode styles for social links */
.dark-mode .social-link {
  background-color: #2a2a2a;
}

.dark-mode .social-link:hover {
  background-color: #646cff;
}

/* Dark Mode Styles */
.dark-mode .skill-card,
.dark-mode .project-card,
.dark-mode .timeline-item,
.dark-mode .contact-info {
  background-color: #2a2a2a;
}

.dark-mode .skill-level,
.dark-mode .timeline-content h4,
.dark-mode .timeline-content .period {
  color: #aaa;
}

.dark-mode .form-group input,
.dark-mode .form-group textarea {
  background-color: #2a2a2a;
  border-color: #444;
  color: white;
}

/* Animations */
.animate-title {
  margin: 0;
  animation: slideIn 1s ease-out;
}

.animate-subtitle {
  animation: slideIn 1s ease-out 0.2s backwards;
}

/* Animation for timeline items */
.fade-in {
  animation: fadeIn 0.5s ease-out forwards;
  opacity: 0;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .contact-container {
    grid-template-columns: 1fr;
  }
  
  .timeline-item {
    margin-left: 1rem;
  }
  
  .timeline-item::before {
    left: -1.5rem;
  }
}

</style>
