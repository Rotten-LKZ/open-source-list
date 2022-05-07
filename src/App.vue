<script setup lang="ts">
import TranslateIcon from './components/icons/IconTranslate.vue';
import Card from './components/Card.vue';
import { ref, watch } from 'vue';
import projects from './assets/projects.json';

const isEnglish = ref(false);

watch(isEnglish, value => {
  document.title = value ? "RotCool's open source project list" : "LKZ 烂裤子的开源项目列表"
  document.documentElement.setAttribute('lang', value ? 'en' : 'zh');
});

function toggleLang() {
  isEnglish.value = !isEnglish.value;
}

function getTrans(key: string, con?: any): string {
  const keys = key.split('.');
  let project: any = con || projects;
  for (let i = 0; i < keys.length; i++) {
    if (i === keys.length - 1) {
      const res = isEnglish.value ? project[keys[i]].en : project[keys[i]].zh;
      if (res === undefined)
        return project[keys[i]];
      return res
    } else {
      project = project[keys[i]];
    }
  }
  return "";
}
</script>

<template>
  <header>
    <TranslateIcon class="icon-translate" @click="toggleLang" :title="getTrans('transTitle')" />
    <h1>{{ getTrans('title') }}</h1>
    <p>{{ getTrans('intro') }}</p>
  </header>

  <main>
    <Card v-for="(value, index) of projects.projects" :key="index" :title="getTrans('title', value)" :intro="getTrans('intro', value)" :link="value.link" :github="value.github" />
  </main>
</template>

<style>
body {
  padding: 0;
  margin: 0;
}

.icon-translate {
  position: absolute;
  right: 40px;
  top: 40px;
  transform: scale(2.2);
}

.icon-translate:hover {
  cursor: pointer;
}

header {
  width: 100%;
  text-align: center;
}

main {
  display: flex;
  flex-wrap: wrap;
  max-width: 1000px;
  width: 80%;
  margin: 0 auto;
}
</style>