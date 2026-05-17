<script setup>
const foodCategories = [
  {
    title: '✅ 优质蛋白质',
    items: [
      { name: '鸡胸肉', desc: '31g/100g，水煮/慢煎' },
      { name: '鸡蛋（全蛋）', desc: '每天 2-3 个 + 额外蛋白' },
      { name: '三文鱼', desc: '富含 Omega-3' },
      { name: '希腊酸奶', desc: '加坚果做加餐' },
      { name: '瘦牛肉/虾仁', desc: '高蛋白低脂肪' }
    ]
  },
  {
    title: '✅ 优质碳水',
    items: [
      { name: '糙米/藜麦', desc: '低 GI，持续供能' },
      { name: '红薯/紫薯', desc: '膳食纤维丰富' },
      { name: '纯燕麦', desc: '早餐首选，饱腹感强' },
      { name: '全麦面包', desc: '训练后补充' },
      { name: '香蕉', desc: '训练前后快速补充糖原' }
    ]
  },
  {
    title: '✅ 优质脂肪',
    items: [
      { name: '牛油果', desc: '半个/天' },
      { name: '混合坚果', desc: '一小把/天' },
      { name: '橄榄油', desc: '凉拌沙拉首选' },
      { name: '深海鱼油', desc: '抗炎恢复' }
    ]
  }
];

const avoidFoods = [
  { name: '含糖饮料', desc: '奶茶、可乐、果汁 (空热量，极易囤积内脏脂肪)' },
  { name: '精加工食品', desc: '薯片、饼干、蛋糕 (高热量密度，容易过量)' },
  { name: '油炸食品', desc: '炸鸡、薯条 (反式脂肪炸弹)' },
  { name: '酒精', desc: '啤酒、白酒 (抑制脂肪代谢，促进腹部囤脂)' }
];
</script>

<template>
  <section class="section scroll-animate" id="diet-guide">
    <div class="container">
      <h2 class="section-title">科学饮食 <span>指南与食谱</span></h2>
      
      <div class="diet-content">
        <!-- 推荐食物 -->
        <div class="food-lists">
          <div class="food-category glass-panel" v-for="(cat, i) in foodCategories" :key="i">
            <h3 class="cat-title">{{ cat.title }}</h3>
            <ul class="food-items">
              <li v-for="(item, j) in cat.items" :key="j">
                <strong>{{ item.name }}</strong>
                <span>{{ item.desc }}</span>
              </li>
            </ul>
          </div>
          
          <div class="food-category glass-panel avoid-panel">
            <h3 class="cat-title error-text">❌ 必须远离的食物</h3>
            <ul class="food-items">
              <li v-for="(item, j) in avoidFoods" :key="j">
                <strong>{{ item.name }}</strong>
                <span>{{ item.desc }}</span>
              </li>
            </ul>
          </div>
        </div>

        <!-- 一日食谱示例 -->
        <div class="meal-plan glass-panel">
          <h3 class="meal-plan-title">🍽️ 一日饮食示例 (减脂期 ~2050 kcal)</h3>
          
          <div class="meal-timeline">
            <div class="meal-slot">
              <div class="meal-time">🌅 早餐 (7:00)</div>
              <div class="meal-food">燕麦 50g + 牛奶 250ml + 蓝莓一把<br>水煮蛋 2 个（全蛋）+ 1 个蛋白</div>
              <div class="meal-cals">约 450 kcal</div>
            </div>
            
            <div class="meal-slot">
              <div class="meal-time">🌞 午餐 (12:00)</div>
              <div class="meal-food">糙米 100g（熟重 200g）<br>鸡胸肉 150g（黑椒煎）<br>西兰花 + 彩椒 200g（少油炒）</div>
              <div class="meal-cals">约 550 kcal</div>
            </div>
            
            <div class="meal-slot">
              <div class="meal-time">🍌 训练前 (15:30)</div>
              <div class="meal-food">香蕉 1 根 + 希腊酸奶 150g</div>
              <div class="meal-cals">约 200 kcal</div>
            </div>
            
            <div class="meal-slot highlight-slot">
              <div class="meal-time">🏋️ 训练 (16:30 - 17:30)</div>
            </div>
            
            <div class="meal-slot">
              <div class="meal-time">🥤 训练后 (17:30)</div>
              <div class="meal-food">乳清蛋白 1 勺 + 全麦面包 2 片</div>
              <div class="meal-cals">约 300 kcal</div>
            </div>
            
            <div class="meal-slot">
              <div class="meal-time">🌙 晚餐 (19:00)</div>
              <div class="meal-food">三文鱼 120g（煎）<br>红薯 100g<br>生菜沙拉（橄榄油 + 柠檬汁）</div>
              <div class="meal-cals">约 500 kcal</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.diet-content {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.food-lists {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 24px;
}

.food-category {
  padding: 24px;
}

.avoid-panel {
  border: 1px solid rgba(255, 71, 87, 0.3);
  background: linear-gradient(180deg, rgba(255,255,255,0.9), rgba(255,71,87,0.05));
}

.cat-title {
  font-size: 1.1rem;
  margin-bottom: 16px;
  border-bottom: 1px solid rgba(0,0,0,0.1);
  padding-bottom: 8px;
}

.error-text {
  color: #ff4757;
}

.food-items {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.food-items li {
  display: flex;
  flex-direction: column;
  font-size: 0.95rem;
}

.food-items li span {
  font-size: 0.8rem;
  color: var(--text-muted);
}

.meal-plan {
  padding: 40px;
  background: linear-gradient(135deg, rgba(255,255,255,0.9), rgba(255,165,0,0.1));
}

.meal-plan-title {
  font-size: 1.5rem;
  color: var(--primary-color);
  margin-bottom: 32px;
  text-align: center;
}

.meal-timeline {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 700px;
  margin: 0 auto;
}

.meal-slot {
  display: grid;
  grid-template-columns: 140px 1fr 100px;
  align-items: center;
  gap: 24px;
  padding: 16px 24px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.03);
}

.highlight-slot {
  background: var(--primary-color);
  color: white;
  text-align: center;
  display: block;
  font-weight: 700;
  font-size: 1.1rem;
}

.meal-time {
  font-weight: 700;
  color: var(--primary-color);
}

.meal-food {
  color: var(--text-main);
  line-height: 1.5;
}

.meal-cals {
  font-weight: 600;
  color: var(--text-muted);
  text-align: right;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .meal-slot {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 8px;
  }
  .meal-cals {
    text-align: center;
  }
}
</style>
