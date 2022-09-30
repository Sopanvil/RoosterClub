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
<style lang="scss">
@import "assets/styles/fonts.css";
@import "reset-css";

@keyframes text-bright {
  from {
    text-shadow: 0 0 10px#ffcc0021;
    
  }

  to {
    text-shadow: 0 0 10px#ffcb00;
  }
}
.yellow {
  color: #ffcb00;
  animation-duration: 3s;
  animation-name: text-bright;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}
body {
  font-family: "Kumbh Sans", sans-serif;
  font-weight: 500;
  background: #0c0d11;
  color: #fff;
  &::-webkit-scrollbar {
    width: 5px;
  }

  &::-webkit-scrollbar-track {
    box-shadow: inset 0 0 6px #0000004d;
  }

  &::-webkit-scrollbar-thumb {
    background-color: #a9a9a9;
    outline: 1px solid #708090;
  }
}
</style>
