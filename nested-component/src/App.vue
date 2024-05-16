<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/clockcalendar">Clock&Calendar</router-link>
      <router-link to="/calculator">Calculator</router-link>
    </nav>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
import ClockCalendar from './components/ClockCalendar.vue';
import Calculator from './components/Calculator.vue';

export default {
  name: 'App',
  components: {
    ClockCalendar,
    Calculator,
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
}

nav {
    justify-content: center; 
    align-items: center; 
    width: 100%; 
    
}

nav a {
    margin: 0 2cap; 
    font-weight: 700;
    text-decoration: none; 
    color: #42b983;
}

nav a.router-link-exact-active {
  font-weight: bold;
}

main {
  padding-top: 4em; /* Adjust this value based on the height of the nav bar */
}
</style>
