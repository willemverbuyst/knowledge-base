## Migrating from Create React App to ViteJS

Install dependencies

>yarn add vite @vitejs/plugin-react vite-tsconfig-paths 

Set up vite configuration

__`vite.config.ts`__
```ts
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import viteTsconfigPaths from 'vite-tsconfig-paths';

// https://vitejs.dev/config/
export default ({mode}) => {
  return defineConfig({
	plugins: [react(), viteTsconfigPaths()],
	define: {
	  "process.env.NODE_ENV": `"${mode}"`
	}
  });
}
```

Move `index.html` up from public to root

Add entry point in the body of the html

__`index.html`__
```html 
<script type="module" src="/src/index.tsx"></script>
```

Update typescript configuration

__`tsconfig.json`__
```json
{
  "compilerOptions": {
    "target": "ESNext",
    "lib": ["dom", "dom.iterable", "esnext"],
    "types": ["vite/client"],
    "allowJs": false,
    "skipLibCheck": false,
    "esModuleInterop": false,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "ESNext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": ["src"]
}
```

Create a `vite-env.d.ts` file

__`vite-env.d.ts`__
```ts
/// <reference types="vite/client" />
```


Remove react scripts

> yarn remove react-scripts

Update package.json

__`package.json`__
```json
"scripts": {
  "start": "vite",
  "build": "tsc && vite build",
  "serve": "vite preview"
},
```

Environment variables need to be renamed in the dotenv
CRA:`REACT_APP_`
VITE:`VITE_`

Rename usage:
CREA:`process.env.REACT_APP_`
VITE: `import.meta.env.VITE_`

