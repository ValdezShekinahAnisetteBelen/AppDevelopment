<template>
  <div id="app">
    <v-app>
      <v-banner
        v-if="deferredPrompt"
        color="info"
        dark
        class="text-left"
      >
        Install our Apps 
        
        <template v-slot:actions>
          <v-btn text @click="dismiss">Dismiss</v-btn>
          <v-btn text @click="install">Install</v-btn>
        </template>
      </v-banner>
      <router-view>
        
      </router-view>
    </v-app>
    <div>
      <!-- Your component's template content goes here -->
    </div>
  </div>
</template>

<script>
import Cookies from "js-cookie";

export default {
  name: "App",
  data() {
    return {
      deferredPrompt: null
    };
  },
  mounted() {
    this.loadScripts();
  },
  methods: {
    loadScripts() {
      const scriptUrls = [
        'js/jquery-3.4.1.min.js',
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
        script.src = process.env.BASE_URL + scriptUrl;
        script.async = true;
        head.appendChild(script);
      });
    },
    async dismiss() {
      Cookies.set("add-to-home-screen", null, { expires: 15 });
      this.deferredPrompt = null;
    },
    async install() {
      this.deferredPrompt.prompt();
    },
  },
  created() {
    window.addEventListener("beforeinstallprompt", (e) => {
      e.preventDefault();
      this.deferredPrompt = e;
      if (Cookies.get("add-to-home-screen") === undefined) {
        this.deferredPrompt = e;
      }
    });
    window.addEventListener("appinstalled", () => {
      this.deferredPrompt = null;
    });
  },
};
</script>
