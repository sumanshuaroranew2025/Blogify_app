# Frontend Requirements - React (npm)

## Package Manager
npm (Node Package Manager)

---

## Prerequisites
| Requirement | Version |
|-------------|---------|
| Node.js | 18.x or higher |
| npm | 9.x or higher |

---

## Dependencies (package.json)

### Production Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| react | ^19.0.0 | React library for building UI |
| react-dom | ^19.0.0 | React DOM rendering |
| react-router-dom | ^7.9.6 | Client-side routing |
| axios | ^1.13.2 | HTTP client for API calls |
| @radix-ui/react-dialog | ^1.1.6 | Accessible dialog component |
| @react-oauth/google | ^0.12.1 | Google OAuth integration |
| @shadcn/ui | ^0.0.4 | UI component library |
| shadcn-ui | ^0.9.4 | UI component library |
| class-variance-authority | ^0.7.1 | CSS class composition |
| clsx | ^2.1.1 | Utility for constructing className strings |
| dotenv | ^16.4.7 | Environment variable management |
| framer-motion | ^12.6.3 | Animation library |
| jwt-decode | ^4.0.0 | JWT token decoding |
| lucide-react | ^0.475.0 | Icon library |
| react-hot-toast | ^2.5.2 | Toast notifications |
| react-toastify | ^11.0.5 | Toast notifications |
| tailwind-variants | ^0.3.1 | Tailwind CSS variants |

### Development Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| vite | ^6.1.0 | Build tool and dev server |
| @vitejs/plugin-react | ^4.3.4 | Vite plugin for React |
| tailwindcss | ^3.4.17 | Utility-first CSS framework |
| postcss | ^8.5.3 | CSS post-processor |
| autoprefixer | ^10.4.20 | PostCSS plugin for vendor prefixes |
| eslint | ^9.19.0 | JavaScript linter |
| @eslint/js | ^9.19.0 | ESLint JavaScript configuration |
| eslint-plugin-react | ^7.37.4 | ESLint React rules |
| eslint-plugin-react-hooks | ^5.0.0 | ESLint React Hooks rules |
| eslint-plugin-react-refresh | ^0.4.18 | ESLint React Refresh rules |
| globals | ^15.14.0 | Global variables for ESLint |
| @types/react | ^19.0.8 | TypeScript types for React |
| @types/react-dom | ^19.0.3 | TypeScript types for React DOM |

---

## Full package.json

```json
{
  "name": "blog-frontend",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "@radix-ui/react-dialog": "^1.1.6",
    "@react-oauth/google": "^0.12.1",
    "@shadcn/ui": "^0.0.4",
    "axios": "^1.13.2",
    "class-variance-authority": "^0.7.1",
    "clsx": "^2.1.1",
    "dotenv": "^16.4.7",
    "framer-motion": "^12.6.3",
    "jwt-decode": "^4.0.0",
    "lucide-react": "^0.475.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "react-hot-toast": "^2.5.2",
    "react-router-dom": "^7.9.6",
    "react-toastify": "^11.0.5",
    "shadcn-ui": "^0.9.4",
    "tailwind-variants": "^0.3.1"
  },
  "devDependencies": {
    "@eslint/js": "^9.19.0",
    "@types/react": "^19.0.8",
    "@types/react-dom": "^19.0.3",
    "@vitejs/plugin-react": "^4.3.4",
    "autoprefixer": "^10.4.20",
    "eslint": "^9.19.0",
    "eslint-plugin-react": "^7.37.4",
    "eslint-plugin-react-hooks": "^5.0.0",
    "eslint-plugin-react-refresh": "^0.4.18",
    "globals": "^15.14.0",
    "postcss": "^8.5.3",
    "tailwindcss": "^3.4.17",
    "vite": "^6.1.0"
  }
}
```

---

## Installation Command

```bash
cd blog-frontend
npm install
```

---

## Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server (http://localhost:5173) |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |
| `npm run lint` | Run ESLint |

---

## Dependencies by Category

### Core React
- react
- react-dom
- react-router-dom

### UI Components
- @radix-ui/react-dialog
- @shadcn/ui
- shadcn-ui
- lucide-react

### Styling
- tailwindcss
- postcss
- autoprefixer
- class-variance-authority
- clsx
- tailwind-variants

### HTTP & Data
- axios
- jwt-decode

### Animations
- framer-motion

### Notifications
- react-hot-toast
- react-toastify

### Authentication
- @react-oauth/google

### Development Tools
- vite
- eslint
- @vitejs/plugin-react

---

*Generated for Blogify Frontend*
