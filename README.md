# ⚡ Vite + React + TypeScript + TailwindCSS + shadcn/ui Setup Guide

This README documents how to simply set up a new Vite + React + TypeScript project with Tailwind CSS and Shadcn/ui components from scratch, as of 22<sup>nd</sup>April, 2025.<br><br>

<div align="center" style="display: flex; justify-content: center; gap: 20px;">
  <span style="background: white; border-radius: 12px; padding: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
    <img src="./media/ShadCn.png" width="200" />
  </span>
  <span style="background: black; border-radius: 12px; padding: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
    <img src="./media/React.png" width="200" />
  </span>
    <span style="background: white; border-radius: 12px; padding: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
    <img src="./media/Tailwind.png" width="200" />
  </span>
  <span style="background: white; border-radius: 12px; padding: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
    <img src="./media/TS.png" width="200" />
  </span>
</div>

<br><br>

---

## 🧱 Step 1: Create Project

```bash
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
```

---

## 🌀 Step 2: Install TailwindCSS

```bash
npm install -D tailwindcss@^3.4 postcss@^8 autoprefixer@^10
npx tailwindcss init -p
```

### 🧾 Update `tailwind.config.js`

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### 🧵 Update `src/index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## 🛠️ Step 3: Configure Files

### 🔧 Update `tsconfig.json`

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    },
    "jsx": "react-jsx",
    "esModuleInterop": true
  }
}
```

---

### 🔧 Update `vite.config.json`

```ts
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import path from "path";

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "src"),
    },
  },
});
```

---

## 🧩 Step 4: Install shadcn/ui

```bash
npm install @radix-ui/react-slot class-variance-authority clsx tailwind-variants
npx shadcn@latest init
```

I usually use the following:

- **New York** (Reccomended)
- **Neutral**

---

## 🔘 Step 5: Test a Component

Install the button component:

```bash
npx shadcn@latest add button
```

_Note_: We use --force flag for now.

Update `src/App.tsx` to test the button:

```tsx
import { useState } from "react";
import { Button } from "@/components/ui/button";

function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="p-4 bg-gray-100 min-h-screen flex flex-col items-center justify-center">
      <h1 className="text-2xl font-bold mb-4">
        Vite + React + TypeScript project with Tailwind CSS and Shadcn/ui
        components
      </h1>
      <Button onClick={() => setCount(count + 1)}>Count is {count}</Button>

      <p className="mt-12 text-sm font-thin text-gray-700">
        If you liked this resource, give it a star on{" "}
        <a
          href="https://github.com/Lightxxo/vite-react-typescript-tailwind-shadcn-template"
          target="_blank"
          rel="noopener noreferrer"
          className="text-blue-500 underline"
        >
          GitHub
        </a>
        !
      </p>
    </div>
  );
}

export default App;
```

Start the dev server:

```bash
npm run dev
```

✅ You should see the button styled with Tailwind and shadcn/ui.

---

©️ For future reference only. All steps verified to work as of 22<sup>nd</sup>April, 2025.
