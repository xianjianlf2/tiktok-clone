<script setup lang="ts">
const props = defineProps(['iconString', 'colorString', 'sizeString'])

const { iconString: iconStringRef, colorString: colorStringRef, sizeString: sizeStringRef } = toRefs(props)

const icon = ref('')

if (iconStringRef?.value === 'For You')
  icon.value = 'mdi:home'
if (iconStringRef?.value === 'Following')
  icon.value = 'ci:group'
if (iconStringRef?.value === 'LIVE')
  icon.value = 'ri:live-line'
</script>

<template>
  <div class="w-full flex items-center hover:bg-gray-100 p-2.5 rounded-md">
    <div class="flex items-center lg:mx-0 mx-auto">
      <Icon :name="icon" :color="colorStringRef" :size="sizeStringRef" />
      <span :class="`text-[${colorStringRef}]`" class="lg:block hidden pl-[9px] mt-0.5 font-semibold text-[17px]">
        {{ iconStringRef }}
      </span>
    </div>
  </div>
</template>
