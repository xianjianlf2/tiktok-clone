<template>
  <div
    @mouseenter="isHover(true)"
    @mouseleave="isHover(false)"
    class="relative brightness-50 hover:brightness-[1.1] cursor-pointer"
  >
    <div
      v-if="!isLoaded"
      class="absolute flex items-center justify-center top-0 left-0 aspect-[3/4] w-full object-cover rounded-md bg-black"
    >
      <Icon
        class="animate-spin ml-1"
        name="mingcute:loading-line"
        size="100"
        color="#FFFFFF"
      />
    </div>
    <div>
      <video
        ref="video"
        muted
        loop
        class="aspect-[3/4] object-cover rounded-md"
        src="/sea.mp4"
      />
    </div>
    <div class="px-1">
      <div class="text-gray-700 text-[15px] pt-1 break-words">
        This is some text
      </div>
      <div class="flex items-center -ml-1 text-gray-600 font-bold text-xs">
        <Icon name="gg:loadbar-sound" size="20"></Icon>
        3%
        <Icon name="tabler:alert-circle" class="ml-1" size="16"></Icon>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps(['post'])

const route = useRoute()
const router = useRouter()

let video = ref()
let isLoaded = ref(false)

const onLoadedData = (e: Event) => {
  if (e.target) {
    setTimeout(() => {
      isLoaded.value = true
    }, 200)
  }
}

onMounted(() => {
  if (video.value) {
    video.value.addEventListener('loadeddata', onLoadedData)
  }
})

onBeforeUnmount(() => {
  video.value.pause()
  video.value.currentTime = 0
  video.value.src = ''
})

const isHover = (isHover: boolean) => {
  if (isHover) {
    video.value.play()
  } else {
    video.value.pause()
  }
}
</script>
