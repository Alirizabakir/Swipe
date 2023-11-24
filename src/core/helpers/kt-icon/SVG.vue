<template>
  <div v-html="svgIcon" :class="`d-inline-block ${props.iconClass}`">
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import { useConfigStore } from "@/stores/config";

const store = useConfigStore();
const svgIcon = ref<string>('');

const props = defineProps({
  iconName: { type: String, default: "", required: true },
  iconClass: { type: String, default: "", required: false },
});

onMounted(async () => {
  try {
    // SVG dosyasını fetch ile al
    const response = await fetch(`/public/media/svg/${props.iconName}.svg`);
    const svgContent = await response.text();
    if (svgContent) {
      svgIcon.value = svgContent
    }
  } catch (error) {
    console.error(`SVG import hatası: ${error}`);
  }
});
</script>
