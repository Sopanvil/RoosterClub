<template>
  <Header />
  <router-view />
</template>

<script>
import Header from "./components/Header.vue";
export default {
  components: {
    Header,
  },
};
</script>
<style>
@import 'assets/styles/fonts.css';

.yellow {
  color: #ffcb00;
  text-shadow: 0 0 10px#ffcb00;
}
body {
  font-family: 'Kumbh Sans', sans-serif; 
  font-weight: 500; 
  background: #0C0D11;
  color: #fff;
}
</style>
