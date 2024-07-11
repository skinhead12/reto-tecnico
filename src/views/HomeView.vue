<template>
  <div class="home">
    <AboutMe />
  </div>
</template>

<script>
// @ is an alias to /src
import AboutMe from "@/components/AboutMe.vue";

export default {
  name: "HomeView",
  components: {
    AboutMe,
  },
};
</script>
