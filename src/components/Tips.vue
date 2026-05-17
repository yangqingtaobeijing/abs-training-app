<template>
  <section class="section scroll-animate" id="tips">
    <div class="container">
      <h2 class="section-title">常见误区与 <span>注意事项</span></h2>
      
      <div class="tips-grid">
        <div class="tips-card glass-panel mistake-card">
          <div class="card-icon">❌</div>
          <h3>三大常见误区</h3>
          <ul class="tips-list">
            <li>
              <strong>局部减脂不存在：</strong>
              <p>每天做 500 个卷腹不能减掉肚子上的肥肉。必须通过制造热量缺口来降低全身脂肪。</p>
            </li>
            <li>
              <strong>仰卧起坐不是最优解：</strong>
              <p>传统的仰卧起坐主要锻炼髂腰肌，而且容易对腰椎造成巨大压力，已被多数专业教练淘汰。</p>
            </li>
            <li>
              <strong>零碳水不可取：</strong>
              <p>完全断绝碳水会导致肌肉流失和基础代谢下降，碳水是高强度腹肌训练必不可少的能量来源。</p>
            </li>
          </ul>
        </div>
        
        <div class="tips-card glass-panel focus-card">
          <div class="card-icon">✅</div>
          <h3>核心注意事项</h3>
          <ul class="tips-list">
            <li>
              <strong>控制速度 (Tempo)：</strong>
              <p>推荐 1-1-2 节奏：1秒收缩，1秒顶峰停顿，2秒缓慢离心（下放）。慢速下放是肌肉生长的关键。</p>
            </li>
            <li>
              <strong>渐进超负荷：</strong>
              <p>当你可以轻松完成15次动作时，说明需要增加负重（如抱哑铃）或更换更高难度的动作了。</p>
            </li>
            <li>
              <strong>正确呼吸：</strong>
              <p>发力卷起时呼气，还原下放时吸气。千万不要憋气，以免血压急剧升高。</p>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tips-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
}

.tips-card {
  padding: 40px;
  position: relative;
  overflow: hidden;
}

.tips-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 6px;
}

.mistake-card::before {
  background: #ff4757;
}

.focus-card::before {
  background: #2ed573;
}

.card-icon {
  font-size: 3rem;
  margin-bottom: 16px;
}

.tips-card h3 {
  font-size: 1.5rem;
  margin-bottom: 24px;
}

.tips-list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.tips-list li p {
  color: var(--text-muted);
  font-size: 0.95rem;
  margin-top: 4px;
}

@media (max-width: 900px) {
  .tips-grid {
    grid-template-columns: 1fr;
  }
}
</style>
