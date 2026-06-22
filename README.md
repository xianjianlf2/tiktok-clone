# TikTok Clone

A TikTok-style short-video web app built with **Nuxt 3** — a vertical video feed, auth, video upload with an in-browser image cropper, profile editing, and user/post pages.

## Features

- 🎬 Vertical scrolling video feed (`pages/index.vue`, `PostMain` / `PostUser`)
- 🔐 Auth overlay — register / login (`AuthOverlay`, `Login`, `Register`)
- ⬆️ Video upload with image cropping (`pages/upload`, `vue-advanced-cropper`)
- 👤 Profile pages & edit profile (`pages/profile/[id]`, `EditProfileOverlay`)
- 📄 Single post page (`pages/post/[id]`)
- 💾 Persisted auth/user state via Pinia (`stores/`, `@pinia-plugin-persistedstate`)

## Tech Stack

- [Nuxt 3](https://nuxt.com/) · Vue 3
- [Pinia](https://pinia.vuejs.org/) (+ persistedstate)
- [Tailwind CSS](https://tailwindcss.com/) · nuxt-icon
- axios · vue-advanced-cropper

## Getting Started

```bash
pnpm install
pnpm dev          # http://localhost:3000
```

Build for production:

```bash
pnpm build
pnpm preview
```
