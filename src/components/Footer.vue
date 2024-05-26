<template>
    <q-footer class="footer">
      <q-toolbar>
        <q-toolbar-title class="footer-title">
          &copy; 2024 - je bracelets
        </q-toolbar-title>
        <div class="footer-icons">
          Follow us:
          <q-icon name="facebook" class="footer-icon" />
          <q-icon name="twitter" class="footer-icon"  />
          <q-icon name="instagram" class="footer-icon" />
        </div>
      </q-toolbar>
    </q-footer>
  </template>
  
  <script>
  export default {
    name: 'Footer'
  }
  </script>
  
  <style scoped>
  .footer {
    background-color: rgb(176, 4, 239);
    color: white; 
    font-family: 'Times New Roman', Times, serif;
  }

  .footer-icons {
    color: white; 
  }
  
  </style>
  