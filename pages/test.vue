<script setup lang="ts">
import test from '../test.md?raw'
</script>

<template>
  <div max-w-3xl font-sans>
    <MDC :value="test" tag="article" />
  </div>
</template>
