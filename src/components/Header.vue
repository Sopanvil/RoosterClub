<template>
  <div class="header">
    <div class="container">
      <div class="header-main">
        <router-link to="/" class="header-main-logo">
          <img src="../assets/img/main-logo.png" width="80" />
          <p class="logo-text">
            ROOSTERS <br />
            GAMBLIBG CLUB
          </p>
        </router-link>
        <div class="header-main-links">
          <router-link to="/" class="header-link">Home</router-link>
          <router-link to="/" class="disabled">Roll</router-link>
          <router-link to="/" class="disabled">RoosterRoll</router-link>
          <a href="https://twitter.com/nft_RFC" target="_blank" class="header-link">Twitter</a>
          <a href="https://discord.gg/wBHYJkmpg5" target="_blank" class="header-link"
            >Discord</a
          >
        </div>
      </div>
    </div>
  </div>
  <div class="header-mobile">
    <div class="container">
      <div class="header-mobile-static">
        <router-link to="/" target class="header-mobile-static-logo">
          <img src="../assets/img/main-logo.png" />
          <p class="logo-text">
            ROOSTERS <br />
            GAMBLIBG CLUB
          </p>
        </router-link>
        <div
          class="animated-burger"
          :class="{ open: isOpen }"
          @click="openHeader()"
        >
          <div class="burger-tracer"></div>
          <div class="burger-tracer"></div>
          <div class="burger-tracer"></div>
        </div>
      </div>
    </div>
    <div class="header-mobile-main" :class="{ open: isOpen }">
      <div class="header-mobile-main-links">
        <router-link to="/" class="header-mobile-link">Home</router-link>
        <router-link to="/" class="disabled">Roll</router-link>
        <router-link to="/" class="disabled">RoosterRoll</router-link>
        <a href="https://twitter.com/nft_RFC" target="_blank" class="header-mobile-link"
          >Twitter</a
        >
        <a href="https://discord.gg/wBHYJkmpg5" target="_blank" class="header-mobile-link"
          >Discord</a
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    openHeader() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "/node_modules/modern-normalize/modern-normalize.css";

.header {
  .container {
    width: 100%;
    padding: 10px 0;
  }
  &-main {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1380px;
    margin: 0 auto;
    &-logo {
      display: flex;
      align-items: center;
      color: #f5f5f5;
      text-decoration: none;
      .logo-text {
        margin-left: 15px;
        font-weight: 600;
        font-size: 24px;
      }
    }
    &-links {
      display: flex;
      gap: 0 30px;
      font-size: 20px;
      .header-link {
        color: #f5f5f5;
        padding: 5px 15px;
        background: #00000000;
        border-radius: 5px;
        text-decoration: none;
        transition: 0.2s;
        &:hover {
          background: #f1f1f123;
        }
      }
      .disabled {
        color: #ffffff50;
        padding: 5px 15px;
        background: #00000000;
        border-radius: 5px;
        text-decoration: none;
        cursor: not-allowed;
      }
    }
  }
}
.header-mobile {
  display: none;
  z-index: 1001;
  position: fixed;
  width: 100%;
  .container {
    position: relative;
    width: 100%;
    padding: 10px;
    background-color: #0c0d11;
    z-index: 3;
  }
  &-static {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: space-between;
    z-index: 1;
    &-logo {
      display: flex;
      align-items: center;
      color: #f5f5f5;
      text-decoration: none;
      img {
        width: 50px;
      }
      .logo-text {
        margin-left: 15px;
        font-weight: 600;
        font-size: 18px;
      }
    }
    .animated-burger {
      width: 30px;
      height: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      .burger-tracer {
        width: 100%;
        border: 1px solid#f5f5f5;
        transition: 0.2s;
      }
      &.open {
        .burger-tracer {
          &:nth-child(1) {
            transform: rotate(-45deg) translateX(-6px) translateY(7px);
          }
          &:nth-child(2) {
            opacity: 0;
          }
          &:nth-child(3) {
            transform: rotate(45deg) translateX(-6px) translateY(-7px);
          }
        }
      }
    }
  }
  &-main {
    width: 100%;
    height: 100%;
    position: fixed;
    left: 0;
    right: 0;
    z-index: 1;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    background-color: #0c0d11;
    transform: translateY(-110%);
    transition: 0.4s;
    &-links {
      display: flex;
      flex-direction: column;
      margin-top: 80px;
      gap: 0 30px;
      font-size: 20px;
      .header-mobile-link {
        color: #f5f5f5;
        padding: 10px 15px;
        margin-bottom: 10px;
        background: #00000000;
        text-decoration: none;
        transition: 0.2s;
        &:hover {
          background: #f1f1f123;
        }
      }
      .disabled {
        color: #ffffff50;
        padding: 10px 15px;
        margin-bottom: 10px;
        background: #00000000;
        text-decoration: none;
        cursor: not-allowed;
      }
    }
    &.open {
      transform: translateX(0%);
    }
  }
}
// Media
@media (max-width: 1400px) {
  .header {
    .container {
      padding: 10px;
    }
  }
}
@media (max-width: 970px) {
  .header {
    display: none;
  }
  .header-mobile {
    display: flex;
  }
}
</style>