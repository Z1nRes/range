<template>
    <div class="DateYears">
      <DateYears />
    </div>
  </template>
  
  <script>
  // @ is an alias to /src
  import DateYears from '@/components/DateYears.vue'
  
  export default {
    name: 'DateYearsView',
    components: {
        DateYears
    }
  }
  </script>