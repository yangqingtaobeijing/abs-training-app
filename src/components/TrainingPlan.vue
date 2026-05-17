<script setup>
import { ref } from 'vue';

const activePhase = ref(1);

const phases = [
  {
    id: 1,
    title: '阶段一：基础期 (第 1-3 周)',
    goal: '建立腹肌感知，学会正确发力',
    exercises: [
      { name: '仰卧卷腹', target: '上腹', sets: '3 × 15', rest: '45s' },
      { name: '仰卧举腿', target: '下腹', sets: '3 × 12', rest: '45s' },
      { name: '死虫 (Dead Bug)', target: '腹横肌', sets: '3 × 10', rest: '45s' },
      { name: '平板支撑', target: '全核心', sets: '3 × 45s', rest: '60s' }
    ]
  },
  {
    id: 2,
    title: '阶段二：进阶期 (第 4-6 周)',
    goal: '增加负荷和难度，开始腹肌肥大训练',
    exercises: [
      { name: '悬垂举腿', target: '下腹', sets: '4 × 12', rest: '45s' },
      { name: '负重卷腹', target: '上腹', sets: '4 × 12', rest: '45s' },
      { name: '俄罗斯转体', target: '侧腹', sets: '4 × 15', rest: '45s' },
      { name: '腹肌轮', target: '全核心', sets: '3 × 10', rest: '60s' }
    ]
  },
  {
    id: 3,
    title: '阶段三：强化期 (第 7-8 周)',
    goal: '高强度刺激，超级组训练',
    exercises: [
      { name: '超级组: 悬垂举腿 + 负重卷腹', target: '上下腹', sets: '4 组', rest: '60s' },
      { name: '超级组: 腹肌轮 + 俄罗斯转体', target: '全方位', sets: '4 组', rest: '60s' },
      { name: '收尾: 平板支撑至力竭', target: '全核心', sets: '2 组', rest: '-' }
    ]
  }
];
</script>

<template>
  <section class="section scroll-animate" id="training">
    <div class="container">
      <h2 class="section-title">8周渐进式 <span>训练课表</span></h2>
      
      <div class="phases-nav">
        <button v-for="phase in phases" :key="phase.id" 
                @click="activePhase = phase.id"
                class="phase-tab" :class="{active: activePhase === phase.id}">
          阶段 {{ phase.id }}
        </button>
      </div>
      
      <template v-for="phase in phases" :key="phase.id">
        <div class="phase-content glass-panel" v-if="activePhase === phase.id">
          <h3 class="phase-title">{{ phase.title }}</h3>
          <p class="phase-goal"><strong>🎯 目标：</strong>{{ phase.goal }}</p>
          
          <div class="exercises-grid">
            <div class="exercise-card" v-for="(ex, index) in phase.exercises" :key="index">
              <h4 class="ex-name">{{ ex.name }}</h4>
              <div class="ex-details">
                <span class="badge target-badge">{{ ex.target }}</span>
                <span class="ex-sets"><strong>组数:</strong> {{ ex.sets }}</span>
                <span class="ex-rest"><strong>休息:</strong> {{ ex.rest }}</span>
              </div>
            </div>
          </div>
        </div>
      </template>
    </div>
  </section>
</template>

<style scoped>
.phases-nav {
  display: flex;
  justify-content: center;
  gap: 16px;
  margin-bottom: 32px;
  position: relative;
  z-index: 10;
}

.phase-tab {
  padding: 12px 24px;
  border-radius: 30px;
  border: 2px solid rgba(255,107,0,0.2);
  background: white;
  color: var(--text-muted);
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.phase-tab.active, .phase-tab:hover {
  background: var(--primary-color);
  color: white;
  border-color: var(--primary-color);
  box-shadow: 0 4px 15px rgba(255,107,0,0.3);
}

.phase-content {
  background: rgba(255,255,255,0.9);
  padding: 40px;
}

.phase-title {
  font-size: 1.8rem;
  color: var(--primary-color);
  margin-bottom: 8px;
}

.phase-goal {
  color: var(--text-muted);
  font-size: 1.1rem;
  margin-bottom: 32px;
}

.exercises-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 24px;
}

.exercise-card {
  background: white;
  border: 1px solid rgba(0,0,0,0.05);
  border-radius: 16px;
  padding: 24px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.02);
  transition: transform 0.3s ease;
}

.exercise-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(255,107,0,0.1);
}

.ex-name {
  font-size: 1.25rem;
  margin-bottom: 16px;
}

.ex-details {
  display: flex;
  flex-direction: column;
  gap: 8px;
  font-size: 0.95rem;
  color: var(--text-muted);
}

.target-badge {
  display: inline-block;
  align-self: flex-start;
  padding: 4px 10px;
  background: rgba(255,165,0,0.15);
  color: #d95b00;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 700;
  margin-bottom: 8px;
}

@media (max-width: 768px) {
  .phases-nav {
    flex-direction: column;
  }
  .phase-content {
    padding: 24px;
  }
}
</style>
