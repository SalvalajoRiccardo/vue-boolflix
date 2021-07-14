<template>
  <body>
    <div id="app">
      <Main/>
    </div>
  </body>
</template>

<script>
import Main from "@/components/Main";

export default {
  name: 'App',
  components: {
    Main
  },

  
}
</script>

<style lang="scss">
@import '@/style/commons.scss';
body {
  background-color: #141414;
}
</style>
