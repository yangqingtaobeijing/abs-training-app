<script setup>
const details = [
  {
    id: 'crunch',
    name: '仰卧卷腹 (Crunch)',
    start: '仰卧，双膝弯曲 90°，双手轻放耳侧（不要抱头）。',
    steps: [
      '呼气 → 用腹肌卷起肩胛骨离地（不是坐起来！）',
      '顶峰收缩 1 秒',
      '吸气 → 缓慢下放（2-3 秒）'
    ],
    error: '抱头用力拉脖子、借助惯性弹起、全程做仰卧起坐'
  },
  {
    id: 'leg-raise',
    name: '悬垂举腿 (Hanging Leg Raise)',
    start: '双手正握杠，身体自然悬垂。',
    steps: [
      '呼气 → 腹肌发力将双腿抬至与地面平行（或更高）',
      '顶峰停顿 1 秒',
      '吸气 → 控制下放（不要自由落体）'
    ],
    note: '进阶：直腿举至脚趾碰杠（Toes to Bar）。退阶：屈膝举腿'
  },
  {
    id: 'ab-wheel',
    name: '腹肌轮 (Ab Wheel Rollout)',
    start: '跪姿，双手握轮，置于肩正下方。',
    steps: [
      '吸气 → 缓慢向前推出（保持核心收紧！）',
      '推至身体几乎平行于地面（或你能控制的最远距离）',
      '呼气 → 腹肌发力拉回起始位置'
    ],
    error: '全程下背不能塌！感到下背参与立刻停止'
  }
];
</script>

<template>
  <section class="section scroll-animate" id="details">
    <div class="container">
      <h2 class="section-title">关键动作 <span>细节拆解</span></h2>
      
      <div class="details-grid">
        <div class="detail-card glass-panel" v-for="item in details" :key="item.id">
          <h3 class="detail-name">{{ item.name }}</h3>
          
          <div class="detail-block">
            <span class="block-label">▶ 起始姿势</span>
            <p>{{ item.start }}</p>
          </div>
          
          <div class="detail-block">
            <span class="block-label">▶ 动作过程</span>
            <ol class="step-list">
              <li v-for="(step, i) in item.steps" :key="i">{{ step }}</li>
            </ol>
          </div>
          
          <div class="detail-block alert-block" v-if="item.error">
            <span class="block-label alert-label">❌ 常见错误 / 警告</span>
            <p>{{ item.error }}</p>
          </div>
          
          <div class="detail-block note-block" v-if="item.note">
            <span class="block-label note-label">💡 进退阶说明</span>
            <p>{{ item.note }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.details-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
}

.detail-card {
  padding: 32px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.detail-name {
  font-size: 1.5rem;
  color: var(--primary-color);
  border-bottom: 2px dashed rgba(255,107,0,0.2);
  padding-bottom: 12px;
  margin-bottom: 8px;
}

.block-label {
  display: inline-block;
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--text-main);
  margin-bottom: 8px;
}

.step-list {
  padding-left: 20px;
  color: var(--text-muted);
  font-size: 0.95rem;
  line-height: 1.6;
}

.step-list li {
  margin-bottom: 4px;
}

.alert-block {
  background: rgba(255, 71, 87, 0.05);
  padding: 16px;
  border-radius: 8px;
  border-left: 4px solid #ff4757;
}

.alert-label {
  color: #ff4757;
}

.note-block {
  background: rgba(46, 213, 115, 0.05);
  padding: 16px;
  border-radius: 8px;
  border-left: 4px solid #2ed573;
}

.note-label {
  color: #2ed573;
}
</style>
