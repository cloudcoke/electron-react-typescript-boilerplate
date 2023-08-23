# linux package install (선택 사항)

```bash
sudo apt install libnss3-dev libgdk-pixbuf2.0-dev libgtk-3-dev libxss-dev libasound2 libgconf-2-4 libatk1.0-0
```

https://stackoverflow.com/questions/73008985/sigtrap-when-starting-electron-on-wsl2

# 프로젝트 설정

```bash
npx create-react-app --template typescript [projectName]
```

```bash
cd [projectName]
```

```bash
npm install -D electron
```

# package.json 수정

```json
"main": "electron/main.js",
    "scripts": {
        "start": "react-scripts start",
        "build": "react-scripts build",
        "test": "react-scripts test",
        "eject": "react-scripts eject",
        "react-electron": "BROWSER=none npm run start",
        "electron": "tsc --project tsconfig.electron.json && electron --trace-warnings ."
    },
```

# main.ts 파일 추가

```bash
mkdir electron && code electron/main.ts
```

```js
import { app, BrowserWindow } from "electron"

const createWindow = () => {
    const win = new BrowserWindow({
        width: 800,
        height: 600,
    })

    win.loadURL("http://localhost:3000")
}

app.whenReady().then(() => {
    createWindow()
})
```

# electron.tsconfig.json 파일 추가

```json
{
    "compilerOptions": {
        "target": "es5",
        "module": "commonjs",
        "moduleResolution": "node",
        "sourceMap": true,
        "emitDecoratorMetadata": true,
        "experimentalDecorators": true,
        "removeComments": false,
        "noImplicitAny": false,
        "suppressImplicitAnyIndexErrors": true
    },
    "include": ["electron"]
}
```

# tsconfig.json

```json
{
    "compilerOptions": {
        "target": "es5",
        "lib": ["dom", "dom.iterable", "esnext"],
        "allowJs": true,
        "skipLibCheck": true,
        "esModuleInterop": true,
        "allowSyntheticDefaultImports": true,
        "strict": true,
        "forceConsistentCasingInFileNames": true,
        "noFallthroughCasesInSwitch": true,
        "module": "esnext",
        "moduleResolution": "node",
        "resolveJsonModule": true,
        "isolatedModules": true,
        "noEmit": true,
        "jsx": "react-jsx"
    },
    "include": ["src"]
}
```
