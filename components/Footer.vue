<template>
  <div class="site-container">
    <div class="main-content">
    </div>
    <footer class="mainfooter" role="contentinfo">
      <div class="footer-content">
        <div class="footer-section">
          <h3>{{ $t('pages') }}</h3>
          <ul>
            <li><NuxtLink :to="localePath('/')">{{ $t('home') }}</NuxtLink></li>
            <li><NuxtLink :to="localePath('/socials')">{{ $t('socials') }}</NuxtLink></li>
            <li><NuxtLink :to="localePath('/projects')">{{ $t('projects') }}</NuxtLink></li>
            <li><NuxtLink :to="localePath('/contact')">{{ $t('contact') }}</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h3>{{ $t('importantInformation') }}</h3>
          <ul>
            <li><NuxtLink :to="localePath('/privacy-policy')">{{ $t('privacyPolicy') }}</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h3>{{ $t('externalLinks') }}</h3>
          <ul>
            <li><NuxtLink href="https://files.aranjannson.com" target="_blank" rel="noopener noreferrer">files.aranjannson</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h3>{{ $t('iconsFrom') }}</h3>
          <ul>
            <li><NuxtLink href="https://material.io/resources/icons/?style=round" target="_blank" rel="noopener noreferrer" >Google</NuxtLink></li>
            <li><NuxtLink href="https://icons8.com/" target="_blank" rel="noopener noreferrer" >Icon8</NuxtLink></li>
          </ul>
        </div>
        <div class="footer-section">
          <h3>{{ $t('language') }}</h3>
          <ul>
            <li><NuxtLink :to="switchLocalePath('en')">English</NuxtLink></li>
            <li><NuxtLink :to="switchLocalePath('tr')">Türkçe</NuxtLink></li>
            <li><NuxtLink :to="switchLocalePath('el')">Ελληνικά</NuxtLink></li>
          </ul>
        </div>
      </div>
      <div class="footer-info">
        <p>{{ $t('copyright') }} {{ copyrightRange}} {{ $t('copyrightEnd') }}</p>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';


definePageMeta({
  title: 'Footer',
  description: 'Page Footer',
});

const developmentYear = 2023;
const currentYear = ref(new Date().getFullYear());
const copyrightRange = computed(() => {
  return currentYear.value === developmentYear
      ? `${developmentYear}`
      : `${developmentYear} - ${currentYear.value}`;
});

const localePath = useLocalePath();
const switchLocalePath = useSwitchLocalePath();
</script>

<style scoped>
body {
  margin: 0;
  font-family: Arial, sans-serif;

}

.site-container {
  flex: 1 0 auto;
  display: flex;
  flex-direction: column;
}

.main-content {
  flex: 1;
  padding: 20px;
  max-height: 80vh;
  overflow-y: auto;
}

.mainfooter {
  flex-shrink: 0;
  //background-color: #333;
  background-color: rgba(0, 0, 0, 0.6);
  color: white;
  padding-top: 20px;
  padding-bottom: 10px;
  width: 100%;
  bottom:0;
}

.footer-content {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  flex-wrap: wrap;
}

.footer-section {
  flex: 1 1 250px;
  margin: 0 20px;
  max-width: 300px;
}

.footer-section h3 {
  font-size: 1.2rem;
  margin-bottom: 10px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.5);
  padding-bottom: 5px;
}

.footer-section ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-section ul li {
  margin-bottom: 8px;
}

.footer-info {
  text-align: center;
  margin-top: 20px;
}
</style>