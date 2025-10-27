<script setup lang="ts">
import { ref, computed } from 'vue'
import { resolveSrc, resolveLink } from '../utils'
import { data as rawPosts } from '../../data/events.data'
import NeoNephosDefaultTheme01 from './NeoNephosDefaultTheme01.vue'
import EventsTilesThemeComponent from './EventsTilesThemeComponent.vue'
import { useData } from 'vitepress'

const { frontmatter } = useData()
const now = new Date()

// Filter out future posts
const pastPosts = rawPosts.filter(post => {
  const temp = new Date(post.date)
  temp.setDate(temp.getDate() + 1)
  return temp < now
}).sort((a, b) => new Date(b.date).getTime() - new Date(a.date).getTime());

// Extract unique years
const years = Array.from(
  new Set(pastPosts.map(post => new Date(post.date).getFullYear()))
).sort((a, b) => b - a)

const selectedYear = ref('all')

// Filter posts by selected year
const filteredPosts = computed(() => {
  if (selectedYear.value === 'all') return pastPosts
  return pastPosts.filter(post => {
    const year = new Date(post.date).getFullYear()
    return year.toString() === selectedYear.value
  })
})
</script>

<template>
  <NeoNephosDefaultTheme01 :hero="frontmatter.hero">
    <template #home-hero-after-title-before-end>
      <section>
        <div class="year-filter-container">
          <label for="year-select">Filter by year:</label>
          <select id="year-select" v-model="selectedYear">
            <option value="all">All Years</option>
            <option v-for="year in years" :key="year" :value="year.toString()">
              {{ year }}
            </option>
          </select>
        </div>

        <div class="vp-features">
          <div
            v-for="post in filteredPosts"
            :key="post.url"
            class="vp-feature"
            :style="{ background: post.backgroundhex || '#876296' }"
          >
            <a :href="resolveLink(post.url)" class="vp-feature-link">
              <div class="vp-feature-imgsrc-container">
                <img
                  class="vp-feature-imgsrc"
                  :src="resolveSrc(post.bannerSmall)"
                  :alt="post.name"
                />
                <div class="vp-feature-text-overlay">
                  <h2 class="vp-feature-title">{{ post.title }}</h2>
                  <h3 class="vp-feature-date">{{ post.date }}</h3>
                </div>
              </div>
            </a>
          </div>
        </div>
      </section>
    </template>

    <template #home-hero-after>
      <div class="neonephos-blue-section">
        <div class="neonephos-blue-section-inner">
          <LandingTilesThemeComponent
            :key="frontmatter.title"
            :titleColor="'white'"
            :tiles="frontmatter.tiles"
            :heading="frontmatter.tilesHeading"
          />
        </div>
      </div>
    </template>
  </NeoNephosDefaultTheme01>
</template>

<style scoped>
.year-filter-container {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin: 1rem 0 2rem;
  padding: 0 1rem;
  font-size: 1rem;
  font-weight: 500;
  color: var(--vp-c-text-1);
}

.year-filter-container select {
  padding: 0.4rem 0.8rem;
  font-size: 1rem;
  border-radius: 6px;
  border: 1px solid var(--vp-c-border);
  background-color: var(--vp-c-bg-soft);
  color: var(--vp-c-text-1);
  transition: border-color 0.2s ease;
}

.year-filter-container select:hover {
  border-color: var(--vp-c-brand);
}

/* Existing styles below */

.vp-features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  padding: 1rem;
  max-width: 1000px;
  margin-bottom: 2rem;
}

.vp-feature {
  aspect-ratio: 16 / 9;
  width: 100%;
  max-width: 400px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: transform 0.2s ease;
}

.vp-feature:hover {
  transform: translateY(-4px);
}

.vp-feature-link {
  display: block;
  padding: 0 0rem;
  text-decoration: none;
  color: inherit;
  width: 100%;
  height: 100%;
}

.vp-feature-imgsrc-container {
  position: relative;
  width: 100%;
  height: 100%;
  margin: auto;
}

.vp-feature-imgsrc {
  max-height: 100%;
  max-width: 100%;
  border-radius: 0%;
  object-fit: cover;
  display: block;
}

.vp-feature-text-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 0%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 0.5rem;
  color: white;
  background: rgba(0, 0, 0, 0.4);
}

.vp-feature-title {
  font-size: 1.4rem;
  font-weight: 600;
  color: white;
}

.vp-feature-date {
  font-size: 0.9rem;
  color: white;
}
</style>
