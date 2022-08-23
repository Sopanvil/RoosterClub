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
          <a href="https://twitter.com/nft_RFC" class="header-link">Twitter</a>
          <a href="https://discord.gg/wBHYJkmpg5" class="header-link">Discord</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
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
        cursor: not-allowed;
      }
    }
  }
}
</style>