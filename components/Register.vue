<script setup lang="ts">
const name = ref()
const email = ref()
const password = ref()
const confirmPassword = ref()
const errors = ref()

function register() {}
</script>

<template>
  <div class="text-center text-[28px] mb-4 font-bold">
    Sign up
  </div>

  <div class="px-6 pb-2">
    <TextInput
      v-model:input="name"
      placeholder="Full name"
      input-type="text"
      :auto-focus="true"
      error=""
    />
  </div>
  <div class="px-6 pb-2">
    <TextInput
      v-model:input="email"
      placeholder="Email address"
      input-type="email"
      error=""
    />
  </div>
  <div class="px-6 pb-2">
    <TextInput
      v-model:input="password"
      placeholder="Password"
      input-type="password"
      error=""
    />
  </div>
  <div class="px-6 pb-2">
    <TextInput
      v-model:input="confirmPassword"
      placeholder="Confirm password"
      input-type="password"
      :error="errors && errors.confirmPassword ? errors.confirmPassword[0] : ''"
    />
  </div>

  <div class="px-6 text-[12px] text-gray-600">
    Forgot password?
  </div>

  <div class="px-6 pb-2 mt-6">
    <button
      :disabled="!name || !email || !password || !confirmPassword"
      :class="
        !name || !email || !password || !confirmPassword
          ? 'bg-gray-200'
          : 'bg-[#F02C56]'
      "
      class="w-full text-[17px] font-semibold text-white bg-[#F02C56] py-3 rounded-sm"
      @click="register"
    >
      Sign up
    </button>
  </div>
</template>
