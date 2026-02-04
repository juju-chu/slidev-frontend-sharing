<script setup lang="ts">
import { computed } from "vue";
import { useNav } from "@slidev/client";

const { currentSlideNo, total } = useNav();
const label = computed(() => `${currentSlideNo.value} / ${total.value}`);
</script>

<template>
  <div class="slidev-page-number">
    {{ label }}
  </div>
</template>
