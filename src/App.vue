<template>
  <header>
   <PageNavbar :logo="logo_src" :alt="app_name"/>
  </header>

  <RouterView />
  <PageFooter />
</template>
<script lang="ts">
import PageNavbar from "./components/PageNavbar.vue";
import PageFooter from "./components/PageFooter.vue";
import { defineComponent} from 'vue'


export default defineComponent({
  components:{
    PageNavbar,
    PageFooter
  },
  data(){
    return {
      logo_src: "/assets/logo.png",
      app_name: "Web Currency"
    }
  }
});
</script>

<style>
* {
  font-family: 'Times New Roman', Times, serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.main {
  margin: 50px;
  min-height: 250px;
  
}
</style>
