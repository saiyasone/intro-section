<template>
  <!-- ======== Header ======== -->
  <Header @on-close="setToggle" />

  <!-- ======== Sidebar ======== -->
  <Sidebar :toggle="state.toggle" @on-close="setToggle" />

  <!-- ======== Sidebar ======== -->
  <Hero />
</template>

<script>
import { onMounted, reactive } from "vue";
import Header from "./components/HeaderComponent.vue";
import Sidebar from "./components/SidebarComponent.vue";
import Hero from "./components/HeroComponent.vue";
export default {
  components: {
    Sidebar,
    Header,
    Hero,
  },

  setup() {
    onMounted(() => {
      window.addEventListener("resize", (e) => {
        let width = e.target.innerWidth;
        if (width >= 992) {
          state.toggle = false;
        }
      });
    });

    const state = reactive({
      toggle: false,
    });

    function setToggle() {
      state.toggle = !state.toggle;
    }
    function onEmit() {
      console.log("emit click!");
    }

    return { state, setToggle, onEmit };
  },
};
</script>

<style>
@import url("./assets/css/style.css");
</style>
