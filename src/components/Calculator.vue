<script setup>
import { ref, computed } from 'vue';

const weight = ref(75);
const height = ref(175);
const age = ref(25);
const gender = ref('male'); // male, female
const activityMultiplier = ref(1.55); // 1.2, 1.375, 1.55, 1.725
const goal = ref('cut'); // cut, maintain, bulk

// Mifflin-St Jeor Equation
const bmr = computed(() => {
  let base = 10 * weight.value + 6.25 * height.value - 5 * age.value;
  return gender.value === 'male' ? base + 5 : base - 161;
});

const tdee = computed(() => bmr.value * activityMultiplier.value);

const targetCalories = computed(() => {
  if (goal.value === 'cut') return tdee.value * 0.8;
  if (goal.value === 'bulk') return tdee.value * 1.1;
  return tdee.value;
});

const macros = computed(() => {
  const cals = targetCalories.value;
  // Protein: 35%, Carbs: 40%, Fat: 25% (per the plan)
  const proteinCals = cals * 0.35;
  const carbsCals = cals * 0.40;
  const fatCals = cals * 0.25;
  
  return {
    protein: Math.round(proteinCals / 4), // 4 kcal/g
    carbs: Math.round(carbsCals / 4), // 4 kcal/g
    fat: Math.round(fatCals / 9) // 9 kcal/g
  };
});
</script>

<template>
  <section class="section scroll-animate" id="calculator">
    <div class="container">
      <h2 class="section-title">你的专属饮食 <span>热量计算器</span></h2>
      <div class="calc-wrapper">
        <div class="calc-form glass-panel">
          <h3 class="panel-title">输入基本信息</h3>
          
          <div class="input-row">
            <div class="input-group">
              <label class="input-label">性别</label>
              <select v-model="gender" class="input-field">
                <option value="male">男性</option>
                <option value="female">女性</option>
              </select>
            </div>
            <div class="input-group">
              <label class="input-label">年龄 (岁)</label>
              <input type="number" v-model="age" class="input-field">
            </div>
          </div>
          
          <div class="input-row">
            <div class="input-group">
              <label class="input-label">身高 (cm)</label>
              <input type="number" v-model="height" class="input-field">
            </div>
            <div class="input-group">
              <label class="input-label">体重 (kg)</label>
              <input type="number" v-model="weight" class="input-field">
            </div>
          </div>
          
          <div class="input-group">
            <label class="input-label">日常活动量</label>
            <select v-model="activityMultiplier" class="input-field">
              <option :value="1.2">久坐不动 (办公室工作)</option>
              <option :value="1.375">轻度活动 (每周运动1-3天)</option>
              <option :value="1.55">中度活动 (每周运动3-5天)</option>
              <option :value="1.725">高度活动 (每周运动6-7天)</option>
            </select>
          </div>
          
          <div class="input-group">
            <label class="input-label">当前目标</label>
            <div class="goal-tabs">
              <button class="goal-tab" :class="{active: goal === 'cut'}" @click="goal = 'cut'">减脂 (推荐)</button>
              <button class="goal-tab" :class="{active: goal === 'maintain'}" @click="goal = 'maintain'">维持</button>
              <button class="goal-tab" :class="{active: goal === 'bulk'}" @click="goal = 'bulk'">增肌</button>
            </div>
          </div>
        </div>
        
        <div class="calc-results glass-panel">
          <h3 class="panel-title">计算结果</h3>
          
          <div class="result-highlight">
            <span class="res-label">每日目标热量</span>
            <span class="res-val highlight">{{ Math.round(targetCalories) }} <span>kcal</span></span>
          </div>
          
          <div class="macros-grid">
            <div class="macro-item protein">
              <span class="macro-val">{{ macros.protein }}g</span>
              <span class="macro-label">蛋白质 (35%)</span>
            </div>
            <div class="macro-item carbs">
              <span class="macro-val">{{ macros.carbs }}g</span>
              <span class="macro-label">碳水 (40%)</span>
            </div>
            <div class="macro-item fat">
              <span class="macro-val">{{ macros.fat }}g</span>
              <span class="macro-label">脂肪 (25%)</span>
            </div>
          </div>
          
          <div class="result-details">
            <div class="detail-row">
              <span>基础代谢率 (BMR)</span>
              <span>{{ Math.round(bmr) }} kcal</span>
            </div>
            <div class="detail-row">
              <span>每日总消耗 (TDEE)</span>
              <span>{{ Math.round(tdee) }} kcal</span>
            </div>
          </div>
          
          <div class="diet-tip">
            <strong>💡 饮食提示：</strong> 如果当前体脂 > 18%(男) / 25%(女)，请优先选择“减脂”。不要同时追求减脂和增肌。
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.calc-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
}

.panel-title {
  margin-bottom: 24px;
  font-size: 1.25rem;
}

.input-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.goal-tabs {
  display: flex;
  gap: 8px;
  background: rgba(255,255,255,0.5);
  padding: 4px;
  border-radius: 8px;
  border: 1px solid rgba(0,0,0,0.05);
}

.goal-tab {
  flex: 1;
  padding: 8px;
  border: none;
  background: transparent;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
  color: var(--text-muted);
  transition: all 0.3s ease;
}

.goal-tab.active {
  background: white;
  color: var(--primary-color);
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.calc-results {
  background: linear-gradient(135deg, var(--card-bg), rgba(255,255,255,0.95));
  display: flex;
  flex-direction: column;
}

.result-highlight {
  text-align: center;
  padding: 24px 0;
  border-bottom: 1px solid rgba(0,0,0,0.05);
  margin-bottom: 24px;
}

.res-label {
  display: block;
  font-size: 1rem;
  color: var(--text-muted);
  margin-bottom: 8px;
}

.res-val.highlight {
  font-size: 3.5rem;
  font-weight: 800;
  color: var(--primary-color);
  line-height: 1;
}

.res-val.highlight span {
  font-size: 1.2rem;
  font-weight: 500;
}

.macros-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 32px;
}

.macro-item {
  background: rgba(255,255,255,0.8);
  padding: 16px;
  border-radius: 12px;
  text-align: center;
  border-left: 4px solid #ddd;
}

.macro-item.protein { border-color: #FF6B00; }
.macro-item.carbs { border-color: #FFA500; }
.macro-item.fat { border-color: #FFD166; }

.macro-val {
  display: block;
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-main);
}

.macro-label {
  font-size: 0.8rem;
  color: var(--text-muted);
}

.result-details {
  margin-bottom: 24px;
}

.detail-row {
  display: flex;
  justify-content: space-between;
  padding: 12px 0;
  border-bottom: 1px dashed rgba(0,0,0,0.1);
  color: var(--text-muted);
}

.diet-tip {
  margin-top: auto;
  padding: 16px;
  background: rgba(255, 107, 0, 0.05);
  border-radius: 8px;
  font-size: 0.9rem;
  color: var(--text-main);
  line-height: 1.5;
}

@media (max-width: 900px) {
  .calc-wrapper {
    grid-template-columns: 1fr;
  }
}
</style>
