# api-typescript-project-init

## Install packages 
```sh
npm i express dotenv ts-node
npm i -D typescript @type/express @type/node nodmon
```

## create tsconfig.json
```json
{
  "compilerOptions": {
    "module": "ESNext", // Use ESNext module system (ES modules)
    "target": "ESNext", // Compile to the latest ECMAScript version
    "moduleResolution": "node", // Resolve modules using Node.js style
    "esModuleInterop": true, // Enables interop between ES modules and CommonJS
    "allowSyntheticDefaultImports": true, // Allows default imports from modules with no default export
    "strict": true, // Enables strict type-checking
    "skipLibCheck": true, // Skip type-checking declaration files (faster builds)
    "outDir": "./dist", // Specifies output directory for compiled files
    "baseUrl": "./",
    "paths": {
      "*": ["node_modules/*"]
    },
    "allowImportingTsExtensions": true, // Allows importing TypeScript files without specifying the extension
    "noEmit": true, // Do not emit outputs
  },
  "include": ["src/**/*"] 
}
```

## create nodemon.json
```json
{
  "watch": ["src"],
  "ext": "ts",
  "ignore": ["dist"],
  "exec": "node --env-file .env --import 'data:text/javascript,import { register } from \"node:module\"; import { pathToFileURL } from \"node:url\"; register(\"ts-node/esm\", pathToFileURL(\"./\"));' src/index.ts"
}
```

## config package.json
```json
  "scripts": {
    "dev": "nodemon --stage local",
    "start" : "node --loader ts-node/esm src/index.ts",
    "build": "tsc" 
  },
  "type": "module",
```
