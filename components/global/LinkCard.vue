<script setup lang="ts">
const props = defineProps<{
  source: string
  id: string
}>()

const sourceMap = {
  gh: async (id: string) => {
    await sleep(5000)
    return {
      title: 'github',
      url: `https://github.com/${id}`,
      icon: 'github',
      star: 100,
      description: 'this is a description text',
      color: '#fafafa',
    }
  },
}

const { data, status } = await useAsyncData(() => {
  return sourceMap.gh(props.id)
})
</script>

<template>
  <a target="_blank" :href="data?.url" :style="`background: ${data?.color}`" my-4 block max-w-md border rounded-md p-4 shadow>
    <div v-if="status === 'pending'" flex items-center gap-4>
      <div flex-1>
        <div mb-2 h-3 w-20 rounded-full bg-gray />
        <div h-3 rounded-full bg-gray />
      </div>
      <div>
        <div h-10 w-10 rounded-md bg-gray />
      </div>
    </div>
    <div v-else flex gap-4>
      <div flex-1 items-center gap-4>
        <div flex>
          <div flex-1 pb-1 font-bold>
            {{ data?.title }}
          </div>
          <div flex gap-1 text-xs text-orange-5>
            <div i-carbon:star />
            <div>{{ data?.star }}</div>
          </div>
        </div>
        <div text-xs text-zinc-800>
          {{ data?.description }}
        </div>
      </div>
      <div rounded-md bg-gray-200 p-2>
        <div i-carbon:logo-github text-2xl />
      </div>
    </div>
  </a>
</template>
