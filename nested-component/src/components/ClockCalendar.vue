<template>
    <div class="clock-calendar">
      <div class="clock">
        <h1>{{ time }}</h1>
      </div>
      <div class="calendar">
        <p>{{ date }}</p>
      </div>
      <div class="description">
        <p>This component displays the current time and date.</p>
      </div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted, onUnmounted } from 'vue';
  
  export default {
    name: 'ClockCalendar',
    setup() {
      const time = ref(new Date().toLocaleTimeString());
      const date = ref(new Date().toLocaleDateString());
  
      const updateTime = () => {
        const now = new Date();
        time.value = now.toLocaleTimeString();
        date.value = now.toLocaleDateString();
      };
  
      let timer;
      onMounted(() => {
        timer = setInterval(updateTime, 1000);
      });
  
      onUnmounted(() => {
        clearInterval(timer);
      });
  
      return {
        time,
        date,
      };
    },
  };
  </script>
  
  <style scoped>
  .clock-calendar {

    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: Arial, sans-serif;
  }
  
  .clock, .calendar {
    text-align: center;
  }
  
  .description {
    margin-top: 20px;
  }
  </style>
  