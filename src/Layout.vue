<!-- <template>  
  <div class="flex flex-row">  
    <nav class="w-1/6">  
      <ul class="flex flex-col gap-3">  
        <li>  
          <router-link to="/" class="text-xl underline">首頁</router-link>  
        </li>  
        <li>  
          <router-link to="/about" class="text-xl underline">關於</router-link>  
        </li>  
        <li>  
          <router-link to="/privacy" class="text-xl underline"  
            >隱私權</router-link  
          >  
        </li>  
        <div class="h-full border-r border-gray-400"></div>  
      </ul>  
    
    </nav>  
    <main class="w-3/4">  
      <router-view></router-view>  
    </main>  
  </div>  
  
</template>   -->
<template>
<aside id="default-sidebar" class="flex flex-row" aria-label="Sidebar">
  <div class="w-1/6">
     <ul class="flex flex-col gap-3">
        <li>
           <a  class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group">
              <svg class="w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 22 21">
                 <path d="M16.975 11H10V4.025a1 1 0 0 0-1.066-.998 8.5 8.5 0 1 0 9.039 9.039.999.999 0 0 0-1-1.066h.002Z"/>
                 <path d="M12.5 0c-.157 0-.311.01-.565.027A1 1 0 0 0 11 1.02V10h8.975a1 1 0 0 0 1-.935c.013-.188.028-.374.028-.565A8.51 8.51 0 0 0 12.5 0Z"/>
              </svg>
              <!-- <router-link to="/homework?Dashboard" class="text-xl ">Dashboard</router-link>  -->
              <router-link :to="{ name: 'homework', query: { side_bar_title: 'Home' } }">Home</router-link>  
              <!-- <span class="ms-3">Dashboard</span> -->
           </a>
        </li>
        <li>
           <a  class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 18 18">
                 <path d="M6.143 0H1.857A1.857 1.857 0 0 0 0 1.857v4.286C0 7.169.831 8 1.857 8h4.286A1.857 1.857 0 0 0 8 6.143V1.857A1.857 1.857 0 0 0 6.143 0Zm10 0h-4.286A1.857 1.857 0 0 0 10 1.857v4.286C10 7.169 10.831 8 11.857 8h4.286A1.857 1.857 0 0 0 18 6.143V1.857A1.857 1.857 0 0 0 16.143 0Zm-10 10H1.857A1.857 1.857 0 0 0 0 11.857v4.286C0 17.169.831 18 1.857 18h4.286A1.857 1.857 0 0 0 8 16.143v-4.286A1.857 1.857 0 0 0 6.143 10Zm10 0h-4.286A1.857 1.857 0 0 0 10 11.857v4.286c0 1.026.831 1.857 1.857 1.857h4.286A1.857 1.857 0 0 0 18 16.143v-4.286A1.857 1.857 0 0 0 16.143 10Z"/>
              </svg>
              <router-link :to="{ name: 'homework', query: { side_bar_title: 'Kanbanme' } }" class="text-xl">Kanban</router-link> 
              <span class="inline-flex items-center justify-center px-2 ms-3 text-sm font-medium text-gray-800 bg-gray-100 rounded-full dark:bg-gray-700 dark:text-gray-300">Pro</span>
           </a>
        </li>
     </ul>
  </div>

<main class="w-5/6">  
      <router-view></router-view>  
</main>  
</aside>
</template>