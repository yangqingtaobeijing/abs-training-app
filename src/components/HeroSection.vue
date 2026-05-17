<template>
  <section class="hero-section" id="hero">
    <div class="container hero-content animate-fade-in-up">
      <div class="hero-text">
        <div class="badge">🔥 100% 科学依据</div>
        <h1 class="hero-title">科学练就<br><span>六块腹肌</span></h1>
        <p class="hero-subtitle">腹肌显现 = 低体脂 + 腹肌肥大训练。<br>饮食占 70%，训练占 30%。一份为期8周的完整计划，帮你打造核心力量与清晰线条。</p>
        <div class="hero-actions">
          <a href="#calculator" class="btn btn-primary">计算每日热量</a>
          <a href="#training" class="btn btn-outline">查看训练课表</a>
        </div>
      </div>
      <div class="hero-visual">
        <div class="visual-circle glass-panel">
          <div class="visual-stats">
            <div class="stat-item">
              <span class="stat-val">&lt; 15%</span>
              <span class="stat-label">男体脂目标</span>
            </div>
            <div class="stat-item">
              <span class="stat-val">&lt; 22%</span>
              <span class="stat-label">女体脂目标</span>
            </div>
            <div class="stat-item">
              <span class="stat-val">8 周</span>
              <span class="stat-label">渐进式训练</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  padding: 180px 0 100px;
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.hero-content {
  display: flex;
  align-items: center;
  gap: 60px;
}

.hero-text {
  flex: 1;
}

.badge {
  display: inline-block;
  padding: 6px 12px;
  background: rgba(255, 107, 0, 0.1);
  color: var(--primary-color);
  border-radius: 20px;
  font-weight: 600;
  font-size: 0.9rem;
  margin-bottom: 20px;
}

.hero-title {
  font-size: 4rem;
  margin-bottom: 24px;
}

.hero-title span {
  color: var(--primary-color);
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-subtitle {
  font-size: 1.2rem;
  color: var(--text-muted);
  margin-bottom: 40px;
  max-width: 500px;
}

.hero-actions {
  display: flex;
  gap: 16px;
}

.hero-visual {
  flex: 1;
  position: relative;
  display: flex;
  justify-content: center;
}

.visual-circle {
  width: 100%;
  max-width: 400px;
  aspect-ratio: 1;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.9), rgba(255, 255, 255, 0.4));
  border: 1px solid rgba(255,255,255,0.6);
  position: relative;
}

.visual-circle::before {
  content: '';
  position: absolute;
  inset: -20px;
  border-radius: 50%;
  background: conic-gradient(from 0deg, transparent, rgba(255,107,0,0.2), transparent);
  animation: spin 10s linear infinite;
  z-index: -1;
}

@keyframes spin {
  100% { transform: rotate(360deg); }
}

.visual-stats {
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.stat-item {
  display: flex;
  flex-direction: column;
}

.stat-val {
  font-size: 2rem;
  font-weight: 800;
  color: var(--text-main);
}

.stat-label {
  font-size: 0.9rem;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 1px;
}

@media (max-width: 900px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
  }
  .hero-actions {
    justify-content: center;
  }
  .hero-subtitle {
    margin: 0 auto 40px;
  }
  .hero-title {
    font-size: 3rem;
  }
}
</style>
