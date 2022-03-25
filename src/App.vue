<template>
  <div class="h-full bg-green-100 dark:bg-green-900">
    <div class="flex h-screen">
      <div class="m-auto">
        <div class="border bg-green-300 dark:bg-green-800 rounded-md p-4 shadow-md text-center">
          <h3 class="text-lg text-gray-700 dark:text-gray-200">Supply Power</h3>
          <button id="toggle-btn" type="button" class="rounded-sm p-4 shadow ring-green-700 dark:ring-green-400">
            <svg id="lightIcon" xmlns="http://www.w3.org/2000/svg" class="hidden h-6 w-6 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
            </svg>
            <svg id="darkIcon" xmlns="http://www.w3.org/2000/svg" class="hidden h-6 w-6 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  mounted () {
    var toggleButton = document.getElementById('toggle-btn');
    var lightIcon = document.getElementById('lightIcon');
    var darkIcon = document.getElementById('darkIcon');

    // Now I need to add it to the local storage
    // But first I need to check if it exists
    if (localStorage.getItem('theme-mode')) {
      if (localStorage.getItem('theme-mode') === 'light') {
        lightIcon.classList.remove('hidden');
        document.documentElement.classList.remove('dark');
      } 
      else {
        darkIcon.classList.remove('hidden');
        document.documentElement.classList.add('dark');
      }
    } 
    else {
      // if the mode doesnt exist, it will be set to default
      localStorage.setItem('theme-mode', 'light'); // default will be the light mode
      console.log('Power Installed');
    }

    // wait for click event
    toggleButton.addEventListener('click', () => {
      lightIcon.classList.toggle('hidden');
      darkIcon.classList.toggle('hidden');

      if (lightIcon.classList.contains('hidden')) {
        localStorage.setItem('theme-mode', 'light');
        document.documentElement.classList.remove('dark');
        darkIcon.classList.remove('hidden');
        console.log('Lights On')
      } 
      else {
        localStorage.setItem('theme-mode', 'dark');
        document.documentElement.classList.add('dark');
        lightIcon.classList.remove('hidden');
        console.log('Lights Off')
      }
    });
  },
}
</script>
