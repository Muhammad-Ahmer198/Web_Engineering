Transcripto AI
1. Project Overview
Transcripto AI is a full-stack web application that allows users to upload audio and video files and automatically generate accurate, timestamped captions and transcripts. The platform detects the spoken language, transcribes speech using AI, lets users edit and translate captions into multiple languages, and finally burns the captions permanently into the video.
The application is aimed at students, researchers, content creators, teachers, and business professionals who need fast and reliable captioning without relying on expensive third-party tools.
1.1 Core Purpose
●	Detects the language spoken in an uploaded video automatically.
●	Generates accurate, timestamped captions using AI speech recognition.
●	Allows the user to edit captions and translate them into 12+ languages.
●	Burns the final captions permanently into the video file for download.
2. Key Features
●	Responsive, animated Home Page with hero section and statistics.
●	Upload page supporting audio/video files with drag-and-drop.
●	Automatic language detection and AI-based transcription.
●	Transcript listing and management dashboard.
●	Caption editing and translation into 12+ languages.
●	Secure user authentication (Sign In / Register).
●	About page describing the platform's mission and features.
●	Sticky navigation bar and footer across all pages.
3. Technologies Used
3.1 Frontend
Technology	Purpose
Vue 3	Core frontend framework (Composition API)
Vite	Fast development build tool
Vue Router	Client-side routing (SPA navigation)
Pinia	State management (auth, video/theme stores)
Tailwind CSS	Utility-first styling framework
Axios	HTTP client for API communication

3.2 Backend & AI Services
Technology	Purpose
Node.js / Express	Backend server and REST API
MongoDB / Mongoose	Database and data modeling
Groq Whisper	AI speech-to-text transcription engine
LLaMA 3.3 70B	Caption translation and text processing
Cloudinary	Cloud storage for uploaded videos
FFmpeg	Video processing and caption burning
JWT / bcrypt.js	Authentication and password security
According to the project homepage, the platform advertises support for 12+ languages, an average processing time of under 60 seconds, and 100% Whisper transcription accuracy claims.
4. Application Routing (SPA)
The application uses Vue Router with createWebHistory() to enable clean URLs without hash fragments. All routes are defined inside src/router/index.js, mapping each page component to a URL path such as Home, Upload, Transcripts, Login, Register, and About.
const routes = [
  { path: '/', component: HomeView },
  { path: '/upload', component: UploadView },
  { path: '/transcripts', component: TranscriptView },
  { path: '/login', component: LoginView },
  { path: '/register', component: RegisterView },
  { path: '/about', component: AboutView },
  { path: '/:pathMatch(.*)*', component: NotFound }
]
5. Component Architecture
5.1 Props — FeatureCard.vue
The FeatureCard component accepts three string props — icon, title, and description — and renders them inside a styled card. The parent view (HomeView.vue) passes values directly as attributes, demonstrating one-way parent-to-child data flow.
// FeatureCard.vue
defineProps({
  icon: String,
  title: String,
  description: String
})
5.2 Props — TranscriptCard.vue
TranscriptCard receives five props (filename, language, duration, date, status) and uses a computed property to derive a CSS class name from the status prop — showing reactive, prop-dependent logic inside a child component.
const statusClass = computed(() => {
  if (props.status === 'Completed')  return 'completed'
  if (props.status === 'Processing') return 'processing'
  return 'pending'
})
5.3 Custom Events (Emits) — UploadCard.vue
The UploadCard component uses defineEmits to declare two custom events: file-selected and upload. When a user selects a file, the component emits file-selected with the File object as a payload. When the Upload button is clicked, it emits upload with no payload — demonstrating child-to-parent communication.
const emit = defineEmits(['file-selected', 'upload'])
 
function selectFile(event) {
  selectedFile.value = event.target.files[0]
  emit('file-selected', selectedFile.value)
}
 
function uploadFile() {
  emit('upload')
}
 
6. Project Structure
The screenshot below shows the folder and file organization of the Transcripto AI codebase as viewed in the module dependency graph / project explorer.
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/6254f4e01cee90ccea217a1ba873689e00969b54/a5.jpg)
7. User Interface — Screenshots
7.1 Home Page
The landing page introduces the platform with the tagline "Your videos, captioned instantly" and highlights that it is powered by Groq Whisper and LLaMA 3.3 70B.
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/5b0eb433a8c72879b9edbfc477778a9aaf240ce1/a1.jpg)
7.2 About Page
The About page explains the motivation behind the project and highlights four key selling points: speed, accuracy, multilingual support, and data privacy
![image alt](https://github.com/Muhammad-Ahmer198/Web_Engineering/blob/4decd614e769935f5e3b5a650f0146b2e3bf3f35/a2.jpg)


