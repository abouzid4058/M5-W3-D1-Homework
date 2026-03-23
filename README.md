# m5-w3-d1-homework: Facebook OAuth Login

## Module 5 - Week 3 - Day 1 Homework: React Facebook Login

This React app implements **Facebook OAuth Login** using the `react-facebook-login` library.

---

## What It Does

- Displays a login page with a standard login form AND a Facebook login button
- When the user clicks **"Login with Facebook"**, a Facebook OAuth popup appears
- After successful authentication, the user is redirected to a **Home** component displaying their Facebook profile picture and name
- Uses `useState` to manage login state, FB data, and profile picture
- Runs on HTTPS (required by Facebook OAuth)

---

## Project Structure

```
react-fb_login/
├── public/
│   └── index.html
├── src/
│   ├── App.js       ← All components: App, LoginForm, Home
│   ├── App.css      ← Styling
│   └── index.js     ← React entry point
└── package.json     ← HTTPS start script + dependencies
```

---

## Setup Instructions

### Step 1: Create a Facebook App

1. Go to [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/)
2. Register as a developer if you haven't already
3. Click **Create App** → Select **Consumer** → Click **Continue**
4. Fill in App Display Name: `React_Login` → Click **Create App**
5. From the dashboard, note your **App ID** (shown at the top)

### Step 2: Add Website Platform

1. In your Facebook Developer dashboard, go to **Settings → Basic**
2. Scroll down and click **+ Add Platform**
3. Select **Website**
4. In Site URL, enter: `https://localhost:3000/`
5. Click **Save Changes**

### Step 3: Configure Your App ID

Open `src/App.js` and replace `YOUR_FACEBOOK_APP_ID` with your actual Facebook App ID:

```jsx
<FacebookLogin
  appId="YOUR_ACTUAL_APP_ID_HERE"
  ...
/>
```

### Step 4: Install & Run

```bash
npm install
npm start
```

The app runs on **https://localhost:3000** (HTTPS is required by Facebook).

> You may see a browser security warning for the self-signed certificate — click "Advanced" and proceed anyway.

---

## Key Components

| Component | Description |
|-----------|-------------|
| `App` | Parent component — manages login state, renders login or home view |
| `LoginForm` | Standard name/email login form (UI only) |
| `Home` | Shown after FB login — displays profile picture and welcome message |

## Key Concepts

- **react-facebook-login** — provides the `<FacebookLogin>` button component
- **useState** — manages `login`, `data`, and `picture` states
- **responseFacebook** — callback that receives FB auth response and sets state
- **Conditional rendering** — `{!login && ...}` shows login form; `{login && ...}` shows Home
- **Props destructuring** — `function Home({fbpic, fbdata})` instead of `props.fbpic`
- **HTTPS** — enabled via `"start": "HTTPS=true react-scripts start"` in package.json
