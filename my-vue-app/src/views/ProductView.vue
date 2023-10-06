<template>
    <div>
      <nav class="sidebar">
        <div class="logo d-flex justify-content-between">
          <a href="index-2.html"><img src="img/logo.png" alt></a>
          <div class="sidebar_close_icon d-lg-none">
            <i class="ti-close"></i>
          </div>
        </div>
        <ul id="sidebar_menu">
          <li class="mm-active">
            <a class="has-arrow" href="#" aria-expanded="false">
              <img src="img/menu-icon/dashboard.svg" alt>
              <span>Dashboard</span>
            </a>
            <ul>
              <li><a class="active" href="index-2.html">Directory</a></li>
              <li><a href="index_2.html">Default</a></li>
            </ul>
          </li>
          <li>
            <a class="has-arrow" href="#" aria-expanded="false">
              <img src="img/menu-icon/2.svg" alt>
              <span>Pages</span>
            </a>
            <ul>
              <li><a href="login.html">Login</a></li>
              <li><a href="resister.html">Register</a></li>
              <li><a href="error_400.html">Error 404</a></li>
              <li><a href="error_500.html">Error 500</a></li>
              <li><a href="forgot_pass.html">Forgot Password</a></li>
              <li><a href="gallery.html">Gallery</a></li>
            </ul>
          </li>
          <!-- Add more list items as needed -->
        </ul>
      </nav>
  
      <section class="main_content dashboard_part">
        <!-- Your main content goes here -->
      </section>
  
      <div class="CHAT_MESSAGE_POPUPBOX">
        <!-- Chat popup content goes here -->
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "ProductView",
    mounted() {
      this.loadScripts();
    },
    methods: {
      loadScripts() {
        const scriptUrls = [
          'js/jquery-3.4.1.min.js',  // Remove leading slash
          'js/bootstrap.min.js',
          'js/jquery.countdown.min.js',
          'js/jquery.nice-select.min.js',
          'js/jquery.nicescroll.min.js',
          'js/slick.min.js',
          'js/biolife.framework.js',
          'js/functions.js',
        ];
  
        const head = document.getElementsByTagName('head')[0];
  
        scriptUrls.forEach((scriptUrl) => {
          const script = document.createElement('script');
          script.src = scriptUrl;
          script.async = true;
          head.appendChild(script);
        });
      },
    },
  };
  </script>
  
  <style scoped>
  /* Your CSS styles go here */
  /* Example: */
  /* .my-component {
     background-color: #fff;
     color: #333;
  } */
  </style>
  