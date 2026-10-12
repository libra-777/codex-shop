<script setup>
import { ref, computed } from 'vue'
import { dishes } from '../data/dishes'
const category = ref('all')
const filteredDishes = computed(() => dishes.filter(dish => category.value === 'all' || dish.category === category.value))
</script>

<template>
<section class="menu-section section" id="menu"><div class="section-heading"><div><div class="eyebrow">FROM OUR KITCHEN</div><h2>招牌好菜，道道用心<span>。</span></h2><p>熟悉的味道，认真做。每一道，都值得慢慢品尝。</p></div><span class="section-side">用心做菜 / 好好吃饭</span></div><div class="menu-toolbar"><div class="filters" aria-label="菜品分类"><button :aria-pressed="category === 'all'" @click="category = 'all'">全部菜品</button><button :aria-pressed="category === 'signature'" @click="category = 'signature'">招牌热菜</button><button :aria-pressed="category === 'seasonal'" @click="category = 'seasonal'">时令小菜</button></div><span class="menu-hint">好味不必多言 <span>↘</span></span></div><div class="dish-grid">
<article v-for="dish in filteredDishes" :key="dish.id" class="dish" :data-category="dish.category">
  <div class="dish-image">
    <img :src="dish.image" :alt="dish.alt" loading="lazy">
    <span v-if="dish.tag" class="dish-tag">{{ dish.tag }}</span>
  </div>
  <div class="dish-title"><h3>{{ dish.name }}</h3><span>¥ {{ dish.price }}</span></div>
  <p>{{ dish.description }}</p>
</article>
</div><p class="sample-note">菜品、价格及图片为品牌展示示例，图片仅供氛围参考。</p></section>
</template>
