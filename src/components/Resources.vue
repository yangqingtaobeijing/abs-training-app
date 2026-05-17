<script setup>
const resources = [
  {
    title: 'Athlean-X (Jeff Cavaliere)',
    desc: '拥有物理治疗师背景，强调基于解剖学的腹肌训练。他的《22天腹肌挑战》和《10分钟无器械腹肌》系列在全球极受欢迎。核心观点：动作规范比数量更重要，腹肌显现完全取决于饮食。',
    url: 'https://www.youtube.com/@athleanx/search?query=abs',
    tags: ['动作解剖', '高强度间歇', '无器械训练']
  },
  {
    title: 'Jeff Nippard',
    desc: '自然健美运动员，以纯科学文献和研究为支撑。他在腹肌训练方面的核心观点是“渐进超负荷”：不要只做几百个仰卧起坐，而应该像练胸肌一样，给腹肌加负重（如负重卷腹、悬垂举腿），做到力竭。',
    url: 'https://www.youtube.com/@JeffNippard/search?query=abs',
    tags: ['科学文献', '渐进超负荷', '肌肉肥大']
  },
  {
    title: 'Jeremy Ethier',
    desc: '专注于基于科学的训练和减脂策略。他的视频详细解释了如何通过饮食制造热量缺口来减少顽固的腹部脂肪（内脏脂肪），并指出“局部减脂”的伪科学。',
    url: 'https://www.youtube.com/@JeremyEthier/search?query=belly+fat',
    tags: ['科学减脂', '热量缺口', '营养学']
  }
];
</script>

<template>
  <section class="section scroll-animate" id="resources">
    <div class="container">
      <h2 class="section-title">优质学习 <span>视频资源</span></h2>
      <p class="section-subtitle">为您精选的 YouTube 顶级硬核健身频道，全方位补充腹肌与减脂科学知识。</p>
      
      <div class="resources-grid">
        <a :href="res.url" target="_blank" rel="noopener noreferrer" class="resource-card glass-panel" v-for="(res, i) in resources" :key="i">
          <div class="res-header">
            <h3 class="res-title">{{ res.title }}</h3>
            <span class="res-icon">↗</span>
          </div>
          <p class="res-desc">{{ res.desc }}</p>
          <div class="res-tags">
            <span class="tag" v-for="(tag, j) in res.tags" :key="j">{{ tag }}</span>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section-subtitle {
  text-align: center;
  color: var(--text-muted);
  margin-top: -16px;
  margin-bottom: 40px;
}

.resources-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
}

.resource-card {
  display: flex;
  flex-direction: column;
  padding: 32px;
  text-decoration: none;
  color: inherit;
  transition: all 0.3s ease;
}

.resource-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 30px rgba(255, 107, 0, 0.15);
  border-color: rgba(255, 107, 0, 0.4);
}

.res-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.res-title {
  font-size: 1.4rem;
  color: var(--text-main);
  margin: 0;
  transition: color 0.3s ease;
}

.resource-card:hover .res-title {
  color: var(--primary-color);
}

.res-icon {
  color: var(--primary-color);
  font-weight: bold;
  opacity: 0.5;
  transition: opacity 0.3s ease;
}

.resource-card:hover .res-icon {
  opacity: 1;
}

.res-desc {
  color: var(--text-muted);
  font-size: 0.95rem;
  line-height: 1.6;
  flex-grow: 1;
  margin-bottom: 24px;
}

.res-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tag {
  font-size: 0.8rem;
  padding: 4px 10px;
  background: rgba(255, 107, 0, 0.08);
  color: var(--primary-color);
  border-radius: 12px;
  font-weight: 600;
}
</style>
