# FlowRaz Development Stacks

מסמך זה מתאר את הסטאקים שבשימוש לפיתוח פרויקטים. העתק את הקטע הרלוונטי לתחילת שיחה חדשה עם AI.

---

## Quick Reference (להעתקה לצ'אטים)

```
# FlowRaz Stack Reference

## SaaS Stack (למוצרים עם משתמשים ותשלומים)
- Cloudflare Workers (Backend API)
- D1 Database (SQLite) + KV + R2 Storage
- Stripe Payments
- Drizzle ORM
- React + Vite (Dashboard)
- Multi-tenant architecture
- Example: flowraz-chatbot

## Content Stack (לאתרי תוכן ודפי נחיתה)
- Next.js 15 + App Router + Static Generation
- Tailwind CSS 4
- Hebrew RTL + Fonts: Rubik, Secular One, Karantina
- Components: Header, Footer, WhatsApp, ScrollReveal, Parallax
- Example: israelenduroseries

## Shared
- TypeScript, ESLint
- Dark theme with CSS variables
- Mobile-first responsive
```

---

## SaaS Stack

### מתי להשתמש?
- מוצרי SaaS עם משתמשים
- אפליקציות עם תשלומים
- מערכות Multi-tenant
- אפליקציות עם אימות (Auth)

### טכנולוגיות

| רכיב | טכנולוגיה | תיאור |
|------|-----------|-------|
| **Backend** | Cloudflare Workers | Serverless API |
| **Database** | D1 (SQLite) | Relational database |
| **Cache** | KV Namespace | Sessions, rate limits |
| **Storage** | R2 | Files, documents |
| **Payments** | Stripe | Subscriptions, billing |
| **ORM** | Drizzle | Type-safe SQL |
| **Frontend** | React + Vite | Dashboard SPA |
| **Auth** | JWT + API Keys | Authentication |

### מבנה פרויקט

```
saas-project/
├── src/
│   ├── index.ts              # Main Worker entry
│   ├── api/                  # API routes
│   ├── auth/                 # Authentication
│   ├── billing/              # Stripe integration
│   ├── db/                   # Database schema
│   └── types/                # TypeScript types
├── dashboard/
│   └── src/
│       ├── components/       # React components
│       ├── lib/              # API client
│       └── i18n/             # Translations
├── wrangler.toml             # Cloudflare config
└── schema.sql                # Database schema
```

### פרויקט לדוגמה
- **FlowRaz Chatbot**: `c:\dev\flowraz-chatbot`

---

## Content Stack

### מתי להשתמש?
- דפי נחיתה
- אתרי תדמית לעסקים
- אתרי אירועים
- פורטפוליו
- בלוגים סטטיים
- אתרים עם תוכן עברי RTL

### טכנולוגיות

| רכיב | טכנולוגיה | תיאור |
|------|-----------|-------|
| **Framework** | Next.js 15 | App Router + SSG |
| **Styling** | Tailwind CSS 4 | Utility-first CSS |
| **Language** | TypeScript | Type safety |
| **Hebrew Body** | Rubik | Sharp geometric font |
| **Hebrew Headings** | Secular One | Bold, impactful |
| **English Brand** | Karantina | Industrial style |

### מבנה פרויקט

```
content-website/
├── src/
│   ├── app/
│   │   ├── layout.tsx        # Root layout + fonts
│   │   ├── page.tsx          # Homepage
│   │   ├── globals.css       # Styles + CSS vars
│   │   └── [pages]/          # Additional pages
│   │
│   └── components/
│       ├── layout/
│       │   ├── Header.tsx
│       │   └── Footer.tsx
│       ├── effects/
│       │   ├── ScrollReveal.tsx
│       │   ├── Parallax.tsx
│       │   └── CountUp.tsx
│       └── home/
│           └── [sections].tsx
├── public/images/
├── tailwind.config.ts
└── next.config.ts
```

### הגדרת פונטים (layout.tsx)

```tsx
import { Rubik, Karantina, Secular_One } from "next/font/google";

const rubik = Rubik({
  subsets: ["hebrew", "latin"],
  weight: ["300", "400", "500", "600", "700", "800", "900"],
  variable: "--font-rubik",
  display: "swap",
});

const secularOne = Secular_One({
  subsets: ["hebrew", "latin"],
  weight: ["400"],
  variable: "--font-secular",
  display: "swap",
});

const karantina = Karantina({
  subsets: ["hebrew", "latin"],
  weight: ["400", "700"],
  variable: "--font-karantina",
  display: "swap",
});

// Body className:
// ${rubik.variable} ${secularOne.variable} ${karantina.variable}
```

### משתני CSS (globals.css)

```css
@theme inline {
  /* Colors */
  --color-background: #0a0a0a;
  --color-foreground: #fafafa;
  --color-primary: #4ade80;
  --color-accent: #f97316;

  /* Fonts */
  --font-sans: var(--font-rubik), sans-serif;
  --font-heading: var(--font-karantina), sans-serif;
  --font-heading-he: var(--font-secular), sans-serif;
}

.font-heading-he {
  font-family: var(--font-heading-he);
  font-weight: 400;
}
```

### קומפוננטות מפתח

```tsx
// Hebrew Heading
<h1 className="text-4xl font-heading-he text-foreground">
  כותרת בעברית
</h1>

// ScrollReveal
<ScrollReveal direction="up" delay={200}>
  <div>Content appears on scroll</div>
</ScrollReveal>

// Glass Card
<div className="glass-card rounded-2xl p-8">
  Content
</div>
```

### פרויקט לדוגמה
- **Israel Enduro Series**: `c:\dev\israelenduroseries`

---

## Shared Technologies

| טכנולוגיה | שימוש |
|-----------|-------|
| TypeScript | Type safety בכל הפרויקטים |
| ESLint | Code quality |
| CSS Variables | Theming |
| Dark Theme | עיצוב כהה כברירת מחדל |
| RTL Support | תמיכה בעברית |
| Mobile-first | Responsive design |

---

## Quick Start Commands

### Content Stack
```bash
npx create-next-app@latest my-website --typescript --tailwind --app
cd my-website
npm run dev
```

### SaaS Stack
```bash
npm create cloudflare@latest my-saas
cd my-saas
wrangler d1 create my-db
wrangler dev
```

---

## Example Projects

| פרויקט | סטאק | תיאור | מיקום |
|--------|------|-------|-------|
| FlowRaz Chatbot | SaaS | פלטפורמת צ'אטבוט | `c:\dev\flowraz-chatbot` |
| Israel Enduro | Content | אתר ליגת אנדורו | `c:\dev\israelenduroseries` |

---

*Updated: January 2026*
