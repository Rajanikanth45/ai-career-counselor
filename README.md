# 🚀 AI Career Counselor (RiseStar AI)

An intelligent, full-stack AI career guidance and counseling platform built with **Laravel 12**, **Livewire 3**, **Tailwind CSS**, and **Google Gemini AI**. Designed specifically for secondary school (grades 11–12) and university undergraduate students to discover, evaluate, and navigate their ideal career paths.

---

## 🌟 Key Features

### 1. 🤖 Real-Time AI Career Counselor (CareerDesk Bot)
- **Livewire-Powered Chat**: Seamless real-time interactive counseling session without page reloads.
- **Tailored Persona**: Context-aware guidance adapted to high school streams and university majors.
- **Multi-Turn Context**: Maintains conversational memory with markdown-rendered responses, advice, and tips.

### 2. 📝 Comprehensive Aptitude & Interest Assessments
- **Multi-Category Testing**: Evaluates students across Logical Reasoning, Numerical Ability, and Verbal Aptitude.
- **On-Demand AI Quiz Generation**: Instantly generate dynamic customized quizzes for specific topics, question counts, and difficulty levels powered by Gemini AI.
- **Detailed Scoring Engine**: Instant automated scoring, accuracy breakdown, and category-level diagnostics.

### 3. 🗺️ Personalized AI Career Blueprint & Roadmaps
- **Score-to-Career Mapping**: Algorithmic and AI-driven matching of aptitude results to ideal career options.
- **Strategic Blueprint**: In-depth AI insights analyzing strengths, areas of improvement, and trajectory recommendations.
- **Milestone Explanations**: Interactive career roadmaps with AI explanations for every required education and training milestone.

### 4. 🧭 Career Exploration Directory
- **Extensive Career Database**: Rich catalog covering technology, engineering, healthcare, commerce, design, and emerging sectors.
- **Detailed Profiles**: Eligibility criteria, core skills, recommended entrance exams, top institutions, future industry outlook, and salary ranges.
- **Bookmarking**: Save and organize prospective career paths for quick access.

### 5. 📄 AI Resume Builder
- **Role-Targeted Generation**: Creates tailored, ATS-friendly professional resumes aligned with a chosen target career.
- **Structured Sections**: Auto-generates career summary, relevant skills, project highlights, and coursework.
- **Live Editing**: In-browser editing and saving of generated resume content.

### 6. 🎙️ Interactive AI Mock Interview
- **Dynamic Role-Specific Simulation**: AI acts as a hiring manager or admissions interviewer for any selected career.
- **Multi-Turn Interviewing**: Realistic back-and-forth questioning based on student responses.
- **Actionable Feedback & Scoring**: Comprehensive end-of-interview evaluation covering communication, technical depth, and actionable areas of improvement.

### 7. 📊 AI Skill-Gap Analysis
- **Readiness Assessment**: Evaluates a student's current competencies against target career requirements.
- **Targeted Action Plan**: Recommends specific missing technical/soft skills, high-value certifications, and learning resources.

### 8. 📑 Downloadable PDF Career Reports
- **Executive Career Dossier**: One-click PDF generation powered by DomPDF.
- **Complete Test & Career Summary**: Beautifully styled report containing assessment scores, category breakdowns, matched careers, and counselor remarks.

---

## 🛠️ Tech Stack & Architecture

- **Backend**: [Laravel 12](https://laravel.com/) (PHP 8.2+)
- **Frontend & Reactivity**: [Laravel Livewire 3](https://livewire.laravel.com/), [Alpine.js](https://alpinejs.dev/), [Blade](https://laravel.com/docs/blade)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) & Vite
- **AI Engine**: [Google Gemini API](https://ai.google.dev/) (`gemini-3.1-flash-lite`) via `GEMINI_API_KEY` (supports multiple load-balanced keys)
- **Database**: [MongoDB](https://www.mongodb.com/) (via [`mongodb/laravel-mongodb`](https://github.com/mongodb/laravel-mongodb))
- **PDF Engine**: [Laravel DomPDF](https://github.com/barryvdh/laravel-dompdf)
- **Authentication**: Laravel Breeze with Role-Based Access Control (`student`, `admin`)

---

## 📋 System Requirements

- **PHP**: `^8.2` or higher (with `mongodb`, `mbstring`, `curl`, and `openssl` extensions enabled)
- **Database**: **MongoDB** (Local instance running at `mongodb://127.0.0.1:27017` or MongoDB Atlas cluster)
- **Composer**: `^2.x`
- **Node.js**: `18.x` or higher & **npm**
- **Google Gemini API Key**: Free API key from [Google AI Studio](https://aistudio.google.com/)

---

## ⚡ Quick Start & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/Rajanikanth45/ai-career-counselor.git
cd ai-career-counselor
```

### 2. Install Dependencies
```bash
# Install PHP packages
composer install

# Install frontend npm packages
npm install
```

### 3. Environment Configuration
Copy the example environment file:
```bash
cp .env.example .env
```
Generate the Laravel application key:
```bash
php artisan key:generate
```

Configure your **MongoDB** connection and **Google Gemini API Key** in `.env`:
```env
# MongoDB Database Configuration
DB_CONNECTION=mongodb
DB_URI=mongodb://localhost:27017
# For MongoDB Atlas cloud connection:
# DB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/?retryWrites=true&w=majority
DB_DATABASE=career_platform

# Google Gemini API Key
GEMINI_API_KEY=your_gemini_api_key_here
```
*(Tip: You can provide multiple comma-separated keys for load balancing, e.g., `GEMINI_API_KEY=key1,key2`)*.

### 4. Database Setup & Seeding
Ensure MongoDB is running, then run migrations and seed the pre-configured tests, career database, and sample users:
```bash
php artisan migrate --force
php artisan db:seed
```

### 5. Build Assets & Start Development Server

Run both Vite and Laravel development server:
```bash
# Terminal 1: Run Vite for frontend assets
npm run dev

# Terminal 2: Run Laravel backend
php artisan serve
```

Alternatively, run the bundled dev script:
```bash
composer run dev
```

Visit the application at: **`http://localhost:8000`**

---

## 🔑 Default Test Credentials

After running `php artisan db:seed`, the following accounts are available for testing:

| Role | Email | Password |
| :--- | :--- | :--- |
| **Student** | `student1@example.com` | `password` |
| **Admin** | `admin@example.com` | `password` |
| **Counselor** | `counselor@example.com` | `password` |

*(You can also register a new student account directly from the UI).*

---

## 📂 Project Directory Structure

```text
├── app/
│   ├── Http/Controllers/
│   │   ├── CareerController.php   # Career exploration, blueprint & bookmarking
│   │   ├── ResumeController.php   # AI resume generation & saving
│   │   ├── StudentController.php  # Student dashboard
│   │   └── TestController.php     # Assessment taking, grading & PDF download
│   ├── Livewire/Student/
│   │   ├── ChatCounselor.php      # Live AI career counselor chatbot
│   │   ├── MockInterview.php      # Interactive AI mock interview component
│   │   └── SkillGap.php           # AI skill-gap analyzer component
│   ├── Models/                    # Eloquent models (User, CareerPath, AptitudeTest, etc.)
│   └── Services/
│       ├── AIService.php          # Core Google Gemini API integration
│       └── PDFService.php         # DomPDF report exporter
├── database/
│   ├── migrations/                # Database schema migrations
│   └── seeders/                   # Career data JSONs, question banks & test users
├── resources/
│   └── views/
│       ├── livewire/student/      # Livewire reactive UI templates
│       ├── student/               # Student portal views (dashboard, blueprint, resume)
│       └── layouts/               # Blade layouts & navigation
├── routes/
│   ├── web.php                    # Student & general application routes
│   └── auth.php                   # Breeze authentication routes
└── .env.example                   # Environment configuration template
```

---

## 🧪 Testing

Run PHPUnit tests:
```bash
php artisan test
```

---

## 📄 License

This project is open-sourced under the [MIT License](LICENSE).
