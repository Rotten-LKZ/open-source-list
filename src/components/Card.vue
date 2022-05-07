<script lang="ts" setup>
import GitHubIcon from './icons/IconGitHub.vue';

defineProps<{
  title: string;
  intro: string;
  link: string;
  github: string;
}>()
</script>

<template>
  <div class="card">
    <h2>{{ $props.title }}</h2>
    <p>{{ $props.intro }}</p>
    <span class="bottom-left">
      <a :href="$props.link" target="_blank">{{ $props.link }}</a>
    </span>
    <span class="bottom-right">
      <a :href="$props.github" target="_blank"><GitHubIcon /></a>
    </span>
  </div>
</template>

<style>
.card {
  background-image: linear-gradient( 135deg, #FFF886 10%, #F072B6 100%);
  height: 150px;
  width: 300px;
  border-radius: 10px;
  margin-left: 10px;
  margin-top: 10px;
  padding: 5px 10px;
  transition: all 0.4s ease-in-out 0s;
  z-index: 1;
  position: relative;
}

.card h2, .card p {
  margin-top: 4px;
  margin-bottom: 4px;
}

.card .bottom-left {
  position: absolute;
  bottom: 5px;
  left: 10px;
}

.card .bottom-right {
  position: absolute;
  bottom: 5px;
  right: 10px;
}

.card a {
  outline: none;
  color: #000;
}

.card a:hover {
  cursor: pointer;
}

.card svg:hover {
  cursor: pointer;
}

.card:hover {
  transform: scale(1.2);
  transition: all 0.4s ease-in-out 0s;
  background-image: linear-gradient( 135deg, #FFD3A5 10%, #FD6585 100%);
  z-index: 9999;
}
</style>