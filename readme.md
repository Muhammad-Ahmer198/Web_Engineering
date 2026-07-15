# Transcripto AI - Frontend Report

## Project Overview

Transcripto AI is a Vue 3 web application that allows users to upload audio and video files, process them for transcription, and view or download the generated transcripts.

The application is designed for:

- Students
- Researchers
- Content Creators
- Professionals

---

## Key Features

- Responsive Home Page
- Upload Audio/Video Files
- Transcript Listing
- User Authentication
- About Page
- Sticky Navigation Bar
- Footer Section
---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| Vue 3 | Frontend Framework |
| Vite | Build Tool |
| Vue Router | Client-side Routing |

---

# SPA Routing

The application uses **Vue Router** with `createWebHistory()` to enable clean URLs without hash fragments.

Routes are defined inside:

```text
src/router/index.js
```

Example:

```javascript
import { createRouter, createWebHistory } from 'vue-router'

import HomeView from '../views/HomeView.vue'
import UploadView from '../views/UploadView.vue'
import TranscriptView from '../views/TranscriptView.vue'
import LoginView from '../views/LoginView.vue'
import RegisterView from '../views/RegisterView.vue'
import AboutView from '../views/AboutView.vue'
import NotFound from '../views/NotFound.vue'

const routes = [
  {
    path: '/',component: HomeView
  },
  {
    path: '/upload', component: UploadView
  },
  {
    path: '/transcripts', component: TranscriptView
  },
  {
    path: '/login', component: LoginView
  },
  {
    path: '/register', component: RegisterView
  },
  {
    path: '/about',component: AboutView
  },
  {
    path: '/:pathMatch(.*)*', component: NotFound
  }
]
const router = createRouter({
  history: createWebHistory(),
  routes
})
export default router
```
---

# Project Structure


<img src="./screenshots/Structure.png" alt="Home Page" width="900">



---
# Props – FeatureCard.vue

The FeatureCard component accepts three string props — icon, title, and description — and renders them inside a styled card. The parent view (HomeView.vue) passes values directly as HTML attributes.

**Child Component — FeatureCard.vue (defineProps)**

```javascript
// src/components/home/FeatureCard.vue
<template>
  <div class="card">
    <div class="icon">{{ icon }}</div>
    <h3>{{ title }}</h3>
    <p>{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  icon:        String,
  title:       String,
  description: String
})
</script>
```

**Parent View — HomeView.vue (passing props)**

```javascript
// src/views/HomeView.vue
<FeatureCard
  icon="⚡"
  title="Fast Transcription"
  description="Convert audio files into text within seconds."
/>
<FeatureCard
  icon="🎯"
  title="High Accuracy"
  description="Generate reliable transcripts using AI technology."
/>
<FeatureCard
  icon="📄"
  title="Easy Export"
  description="Download transcripts in multiple formats."
/>
```

# Props – TranscriptCard.vue

TranscriptCard receives five props and uses a computed property to derive a CSS class name from the status prop, demonstrating reactive prop-dependent logic inside a child component.

```javascript
// src/components/transcript/TranscriptCard.vue
<script setup>
import { computed } from 'vue'

const props = defineProps({
  filename: String,
  language: String,
  duration: String,
  date:     String,
  status:   String
})

const statusClass = computed(() => {
  if (props.status === 'Completed')  return 'completed'
  if (props.status === 'Processing') return 'processing'
  return 'pending'
})
</script>
```

TranscriptView.vue loops over a local data array and passes each transcript object's fields as individual props to TranscriptCard using v-for:

```javascript
// src/views/TranscriptView.vue
<TranscriptCard
  v-for="item in transcripts"
  :key="item.id"
  :filename="item.filename"
  :language="item.language"
  :duration="item.duration"
  :date="item.date"
  :status="item.status"
/>
```

# 6.3 Custom Events (Emits) – UploadCard.vue

The UploadCard component uses defineEmits to declare two custom events: file-selected and upload. When a user selects a file, the component emits file-selected with the File object as a payload. When the Upload button is clicked, it emits upload with no payload. The parent view (UploadView.vue) listens for both events using the @event syntax.

**Child Component — UploadCard.vue (defineEmits)**

```javascript
// src/components/upload/UploadCard.vue
<script setup>
import { ref } from 'vue'

const emit = defineEmits(['file-selected', 'upload'])

const fileInput   = ref(null)
const selectedFile = ref(null)

function selectFile(event) {
  selectedFile.value = event.target.files[0]
  emit('file-selected', selectedFile.value)   // ← emits upward with payload
}

function uploadFile() {
  emit('upload')                              // ← emits upward, no payload
}
</script>
```

**Parent View — UploadView.vue (handling emits)**

```javascript
// src/views/UploadView.vue
<UploadCard
  @file-selected="handleFile"
  @upload="startUpload"
/>

<script setup>
import { ref } from 'vue'

const selectedFile = ref(null)

function handleFile(file) {
  selectedFile.value = file       // ← receives the File object from child
}

function startUpload() {
  alert('Frontend Demo: Upload will be implemented in the backend phase.')
}
</script>
```


---

# User Interface

The frontend includes the following pages:

## Home
<img src="./screenshots/home.png" alt="Home Page" width="900">

## About
<img src="./screenshots/about.png" alt="about Page" width="900">

## Upload
<img src="./screenshots/upload.png" alt="upload Page" width="900">

## Transcript
<img src="./screenshots/transcripts.png" alt="transcripts Page" width="900">

## Login
<img src="./screenshots/login.png" alt="login Page" width="900">

## Register
<img src="./screenshots/register.png" alt="register Page" width="900">



---

# Conclusion

The frontend of **Transcripto AI** demonstrates a modular Vue 3 architecture using reusable components, Vue Router for SPA navigation, Props for parent-to-child communication, and Custom Events for child-to-parent communication. The project is responsive, organized, and ready for backend integration.

---

