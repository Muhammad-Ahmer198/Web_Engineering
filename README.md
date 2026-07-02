# Transcripto AI

Transcripto AI is a frontend web application developed using Vue 3 and Vite that converts audio and video files into text transcripts. The project demonstrates a modern Single Page Application (SPA) architecture using Vue Router and reusable Vue components.

---
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/6fbad7d68f1d2fbfff580864427dd6d4dcf6a5cf/a3.jpg)
## Features

- Home Page
- About Page
- Upload Audio/Video Files
- Transcript Management
- Login Page
- Registration Page
- Responsive User Interface
- Vue Router Navigation
- Component-Based Architecture

---

## Technologies

- Vue 3
- Vite
- Vue Router
- JavaScript
- HTML5
- CSS3

---

## Project Structure
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/3e61d7c977b8672fc5416e4d1c8f437487a8bcc7/a8.jpg)
```
src
│
├── assets
├── components
│   ├── Navbar.vue
│   ├── Footer.vue
│   ├── HeroSection.vue
│   ├── UploadCard.vue
│   ├── TranscriptCard.vue
│   └── EmptyState.vue
│
├── router
│   └── index.js
│
├── views
│   ├── HomeView.vue
│   ├── AboutView.vue
│   ├── UploadView.vue
│   ├── TranscriptView.vue
│   ├── LoginView.vue
│   ├── RegisterView.vue
│   └── NotFound.vue
│
├── App.vue
└── main.js
```

---

## Application Pages

### Home

Landing page introducing Transcripto AI.
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/310f77ca1de71e311c6f054a819f4fe338d2b965/a4.jpg)

### About

Displays project overview, mission, vision, and objectives.

### Upload
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/3b1ee1a1d68ace9de26716570bdf9f87c84c8485/a7.jpg)
Allows users to upload supported audio and video files.

Supported formats:

- MP3
- WAV
- MP4
- M4A

### Transcripts

Displays generated transcripts with:

- Status
- Duration
- Language
- Download
- View

### Login
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/ca1a5d52bf92590d13e39b44d183ff7d392fa498/a6.jpg)
Authentication page.

### Register

User registration page.

---

## Vue Router

Routes include:

- /
- /about
- /upload
- /transcripts
- /login
- /register
- *

---

## Component Architecture

- Navbar
- Footer
- HeroSection
- UploadCard
- TranscriptCard
- EmptyState

The project follows reusable component architecture.

---

## Installation

Clone repository

```bash
git clone https://github.com/yourusername/transcripto-ai.git
```

Go inside project

```bash
cd transcripto-ai
```

Install dependencies

```bash
npm install
```

Run development server

```bash
npm run dev
```

Open

```
http://localhost:5173
```

---

## Future Improvements

- Express.js Backend
- MongoDB Database
- JWT Authentication
- Speech-to-Text API
- User Dashboard
- Transcript Search
- File Storage

---

## Screenshots

- Home Page
- About Page
- Upload Page
- Login Page
- Transcript Page

---

## Author

Ahmer Irfan

Department of Software Engineering

University of Sialkot

---

## License

This project is developed for Semester Project (Deliverable 1) at the University of Sialkot.# frontend

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
