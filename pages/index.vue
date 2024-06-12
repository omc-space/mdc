<script setup lang="ts">
import customs from '../customize.md?raw'
</script>

<template>
  <div max-w-3xl font-sans>
    <MDC :value="customs" tag="article" />
  </div>
</template>
