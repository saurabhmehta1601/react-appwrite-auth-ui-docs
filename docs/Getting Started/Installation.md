### Pre-requisites

1. Make sure the appwrite backend is running . To know more about appwrite backend setup , click [ here ](https://appwrite.io/docs/installation) .
2. Make sure you have a project created in appwrite console . To know more about creating a project , click [ here ](https://appwrite.io/docs/getting-started-for-web#createProject) .
3. Get projectId and endpoint from appwrite console .
### 1.Create a new React app with Vitejs 
Run following command in your terminal to create a new React app with [Vitejs](https://vitejs.dev/) and follow prompt to select react template .

#### With NPM
```bash
npm create vite@latest
```
#### With yarn
```bash
yarn create vite
```
### 2. Install dependencies

With NPM 
```bash
npm install appwrite @appwrite.io/pink  react-appwrite-auth-ui
```

With Yarn
```bash
yarn add appwrite @appwrite.io/pink react-appwrite-auth-ui 
```

### 3. Setup AppwriteProvider with Appwrite SDK


```tsx
# main.jsx

import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import './index.css'
// import pink design
import "@appwrite.io/pink"

// initialize Appwrite client and account with Appwrite SDK
import {Client ,Account} from "appwrite"
import { AppwriteAuthUIProvider } from "react-appwrite-auth-ui"

const endpoint = 'https://[HOSTNAME_OR_IP]/v1' // Your API Endpoint
const projectId = '5df5acd0d48c2' // Your project ID

const client = new Client().setEndpoint(endpoint).setProject(projectId)
const account = new Account(client)

// Wrap the App with Appwrite Provider
ReactDOM.createRoot(document.getElementById('root') as HTMLElement).render(
  <React.StrictMode>
    <AppwriteAuthUIProvider client={client} account={account}>
      <App />
    </AppwriteAuthUIProvider>
  </React.StrictMode>,
)

```