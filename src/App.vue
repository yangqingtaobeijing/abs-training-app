<script setup>
import { onMounted } from 'vue';

// Import components
import HeroSection from './components/HeroSection.vue'
import Calculator from './components/Calculator.vue'
import DietGuide from './components/DietGuide.vue'
import TrainingPlan from './components/TrainingPlan.vue'
import ExerciseDetails from './components/ExerciseDetails.vue'
import Tips from './components/Tips.vue'
import Resources from './components/Resources.vue'

onMounted(() => {
  // Simple intersection observer for scroll animations
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-fade-in-up');
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.scroll-animate').forEach((el) => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(40px)';
    el.style.transition = 'opacity 0.8s ease-out, transform 0.8s ease-out';
    observer.observe(el);
  });
});
</script>

<template>
  <div class="app-wrapper">
    <!-- Navbar -->
    <header class="navbar glass-panel">
      <div class="container navbar-content">
        <div class="logo">
          <span class="logo-icon">🔥</span> CoreFit
        </div>
        <nav class="nav-links">
          <a href="#calculator">饮食计算器</a>
          <a href="#diet-guide">饮食食谱</a>
          <a href="#training">8周训练</a>
          <a href="#details">动作拆解</a>
          <a href="#tips">避坑指南</a>
          <a href="#resources">视频资源</a>
        </nav>
      </div>
    </header>

    <main>
      <HeroSection />
      
      <Calculator />
      
      <DietGuide />
      
      <TrainingPlan />
      
      <ExerciseDetails />
      
      <Tips />
      
      <Resources />
    </main>
    
    <footer class="footer">
      <div class="container">
        <p>© 2026 CoreFit - 科学腹肌训练计划. 保持坚持！</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.app-wrapper {
  min-height: 100vh;
}

.navbar {
  position: fixed;
  top: 16px;
  left: 50%;
  transform: translateX(-50%);
  width: 90%;
  max-width: 1000px;
  padding: 12px 24px;
  z-index: 100;
  border-radius: 40px;
  background: rgba(255, 255, 255, 0.7) !important;
  backdrop-filter: blur(20px) !important;
}

.navbar-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0;
}

.logo {
  font-size: 1.25rem;
  font-weight: 800;
  color: var(--primary-color);
  display: flex;
  align-items: center;
  gap: 8px;
}

.nav-links {
  display: flex;
  gap: 24px;
}

.nav-links a {
  color: var(--text-main);
  font-weight: 500;
  font-size: 0.95rem;
}

.nav-links a:hover {
  color: var(--primary-color);
}

.footer {
  text-align: center;
  padding: 40px 0;
  color: var(--text-muted);
  font-size: 0.9rem;
  margin-top: 60px;
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }
}
</style>
