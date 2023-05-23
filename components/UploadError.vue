<script setup lang="ts">
const props = defineProps(['errorType'])

const { errorType: errorTypeRef } = toRefs(props)

const error = ref('')

watch(
  () => errorTypeRef?.value,
  () => {
    if (errorTypeRef?.value === 'caption')
      error.value = 'Maximum  150 characters'
    else if (errorTypeRef?.value === 'bio')
      error.value = 'Maximum 80 characters'
    else if (errorTypeRef?.value === 'file')
      error.value = 'Unsupported file type.Use MP4 instead'
    else
      error.value = ''
  },
)
</script>

<template>
  <div class="w-full relative flex justify-center">
    <div
      class="absolute top-6 z-50 mx-auto bg-black bg-opacity-70 text-white px-14 py-3 rounded-sm"
      :class="errorTypeRef ? 'visible' : 'invisible'"
    >
      {{ error }}
    </div>
  </div>
</template>
