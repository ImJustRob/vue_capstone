<script>
import Header from "./Header.vue";
import Content from "./Content.vue";
import Footer from "./Footer.vue";

export default {
  name: "app",
  components: {
    Header,
    Content,
    Footer,
  },
};
</script>

<template>
  <div>
    <Header />
    <Content />
    <Footer />
  </div>
</template>

<style></style>