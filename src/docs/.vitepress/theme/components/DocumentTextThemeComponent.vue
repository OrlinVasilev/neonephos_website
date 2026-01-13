<script setup lang="ts">
import NeoNephosDefaultTheme01 from './NeoNephosDefaultTheme01.vue'
import LandingTilesThemeComponent from './LandingTilesThemeComponent.vue'
import { useData } from 'vitepress'
console.log("HIER");
const { frontmatter } = useData()
</script>

<template>
  <div >
    <NeoNephosDefaultTheme01 :hero="frontmatter.hero">
      <template #home-hero-after>
        <div v-html="frontmatter.hero?.text" ></div>
        <br>
        <br>
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
  </div>
</template>

<style scoped>
.events-text-container {
  padding: 2rem 1rem;
}


</style>
