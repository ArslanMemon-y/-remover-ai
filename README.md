# CutOut AI — Background Remover

A production-ready AI background remover SaaS app built with Next.js 14, TypeScript, Tailwind CSS, and Framer Motion. Powered by the remove.bg API.

## ✨ Features

- 🤖 AI-powered background removal via remove.bg API
- 🖱️ Drag & drop image upload
- 🔄 Before/After comparison slider
- 💾 HD transparent PNG download
- ✨ Animated processing states
- 📱 Fully responsive (mobile + desktop)
- 🔒 Secure — API key never exposed to client
- 🎨 Premium dark UI with glassmorphism & animations

---

## 🗂️ Project Structure

```
bg-remover/
├── app/
│   ├── api/
│   │   └── remove-background/
│   │       └── route.ts          ← Secure backend API route
│   ├── globals.css               ← Global styles + Tailwind
│   ├── layout.tsx                ← Root layout + toast provider
│   └── page.tsx                  ← Main page with state machine
├── components/
│   ├── AnimatedBackground.tsx    ← Floating blobs & grid
│   ├── FeatureCards.tsx          ← Features section
│   ├── Footer.tsx                ← Site footer
│   ├── HeroSection.tsx           ← Hero with CTA
│   ├── LoadingState.tsx          ← AI processing animation
│   ├── Navbar.tsx                ← Sticky responsive navbar
│   ├── ResultPreview.tsx         ← Before/after + download
│   └── UploadBox.tsx             ← Drag & drop upload zone
├── hooks/
│   └── useBackgroundRemover.ts   ← Custom hook for state management
├── lib/
│   └── utils.ts                  ← Helper functions
├── .env.local.example            ← Environment variable template
├── next.config.mjs
├── tailwind.config.ts
└── tsconfig.json
```

---

## 🚀 Quick Start

### 1. Clone & Install

```bash
# Clone or create the project
cd bg-remover

# Install dependencies
npm install
```

### 2. Set Up Environment Variables

```bash
# Copy the example file
cp .env.local.example .env.local
```

Open `.env.local` and add your remove.bg API key:

```env
REMOVE_BG_API_KEY=your_actual_api_key_here
```

**🔑 Where to get your API key:**
1. Go to [https://www.remove.bg/api](https://www.remove.bg/api)
2. Sign up / log in
3. Navigate to **API Keys** in your dashboard
4. Copy your API key and paste it into `.env.local`

> ⚠️ **IMPORTANT:** Never commit `.env.local` to git. It's already in `.gitignore`.
> The API key is only used server-side in `app/api/remove-background/route.ts` — it is NEVER exposed to the browser.

### 3. Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📦 NPM Packages

Install all dependencies with:

```bash
npm install next react react-dom typescript tailwindcss postcss autoprefixer framer-motion lucide-react react-dropzone react-hot-toast form-data axios @types/node @types/react @types/react-dom eslint eslint-config-next
```

Or use the package.json already included:

```bash
npm install
```

---

## 🏗️ Build for Production

```bash
npm run build
npm start
```

---

## ☁️ Deploy to Vercel

### Option 1: Vercel CLI (Recommended)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Set your environment variable
vercel env add REMOVE_BG_API_KEY
```

### Option 2: Vercel Dashboard

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com) → **New Project**
3. Import your GitHub repository
4. Before deploying, add the environment variable:
   - Go to **Settings → Environment Variables**
   - Name: `REMOVE_BG_API_KEY`
   - Value: `your_actual_api_key`
   - Environment: Production (and Preview if needed)
5. Click **Deploy**

> ✅ Vercel automatically detects Next.js and configures everything correctly.

---

## 🔐 API Key Security

The remove.bg API key is protected at multiple levels:

| Layer | Protection |
|-------|-----------|
| `.env.local` | Not committed to git |
| `NEXT_PUBLIC_` prefix **not used** | Key stays server-only |
| API route (`/app/api/...`) | Only runs on Node.js server |
| Client code | Never sees the API key |

The flow is:
```
Browser → /api/remove-background (Next.js server) → remove.bg API
```

---

## 🎨 Tech Stack

| Technology | Purpose |
|-----------|---------|
| Next.js 14 (App Router) | Framework |
| TypeScript | Type safety |
| Tailwind CSS | Styling |
| Framer Motion | Animations |
| Lucide React | Icons |
| React Dropzone | File upload |
| React Hot Toast | Notifications |
| remove.bg API | AI processing |

---

## 🐛 Troubleshooting

**"API key not configured" error**
→ Make sure `.env.local` exists with `REMOVE_BG_API_KEY=your_key`

**"Invalid API key" error**
→ Double-check your remove.bg API key at [remove.bg dashboard](https://www.remove.bg/dashboard#api-key)

**"API credit limit reached" error**
→ Free tier gives 50 credits/month. Purchase more at remove.bg

**Image too large error**
→ Max upload size is 10MB. Compress your image first.

**Fonts not loading**
→ Requires internet connection (fonts load from Google Fonts & Fontshare CDN)
