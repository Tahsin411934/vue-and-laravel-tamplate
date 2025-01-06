## 1. Install Laravel
First, create a new Laravel project:
```bash
composer create-project laravel/laravel laravel-vue-router
```
Navigate to the project directory:
```bash
cd laravel-vue-router
```

## 2. Install Frontend Dependencies
Install Node.js dependencies and Laravel's Vite setup for frontend development:
```bash
npm install
```

## 3. Install Vue and Vue Router
Install Vue.js and Vue Router:
```bash
npm install vue@3 vue-router@4 
```

## 4. Configure Laravel Vite for Vue
Install the @vitejs/plugin-vue package to enable Vue support with Vite:
```bash
npm install --save-dev @vitejs/plugin-vue
```
Update your vite.config.js file to include Vue:
```bash
import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';
import laravel from 'laravel-vite-plugin';

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
        vue(),
    ],
});
```
## 5. Set Up Vue Router
Create a resources/js/router/index.js file for Vue Router configuration:
```bash
import { createRouter, createWebHistory } from 'vue-router';
import Home from '../views/Home.vue';
import About from '../views/About.vue';

const routes = [
    { path: '/', name: 'Home', component: Home },
    { path: '/about', name: 'About', component: About },
];

const router = createRouter({
    history: createWebHistory(),
    routes,
});

export default router;

```

## 6. Create Vue Components
Create a resources/js/views folder and add the Home.vue and About.vue components:
Home.vue:
```bash

<template>
  <div>
    <h1>Welcome to the Home Page</h1>
  </div>
</template>
```
About.vue
```bash
<template>
  <div>
    <h1>About Us</h1>
  </div>
</template>

```

## 7. Set Up the Vue App 
Update the resources/js/app.js file to initialize Vue and Vue Router:
```bash
import { createApp } from 'vue';
import App from './App.vue';
import router from './router';

createApp(App)
    .use(router)
    .mount('#app');
```
Create an App.vue file in resources/js:
``bash
<template>
  <div>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view></router-view>
  </div>
</template>
```

## 8. Update Blade File
In the resources/views/welcome.blade.php file, replace the content with a root element for Vue:
```bash 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laravel Vue Router</title>
    @vite('resources/css/app.css')
</head>
<body>
    <div id="app"></div>
    @vite('resources/js/app.js')
</body>
</html>
```

## 9. Build and Run the Project
Run the following commands to build and serve the application:
```bash 
npm run dev
php artisan serve
```

