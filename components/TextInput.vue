<script setup lang="ts">
const props = defineProps([
  'input',
  'placeholder',
  'inputType',
  'max',
  'autoFocus',
  'error',
])

const emit = defineEmits(['update:input'])

const { input: inputRef, placeholder: placeholderRef, inputType: inputTypeRef, max: maxRef, autoFocus: autoFocusRef, error: errorRef } = toRefs(props)

onMounted(() => {
  if (autoFocusRef?.value) {
    const input = document.getElementById(`input-${placeholderRef?.value}`)
    input?.focus()
  }
})

const inputComputed = computed({
  get: () => inputRef?.value,
  set: val => emit('update:input', val),
})
</script>

<template>
  <div>
    <input
      :id="`input-${placeholderRef}`" v-model="inputComputed" :placeholder="placeholderRef"
      class="block w-full bg-[#F1F1F2] text-gray-800 border border-gray-300 rounded-md py-2.5 px-3 focus:outline-none"
      :type="inputTypeRef" autocomplete="off" :maxlength="maxRef"
    >
    <span v-if="errorRef" class="text-red-500 text-[14px] font-semibold">
      {{ errorRef }}
    </span>
  </div>
</template>
