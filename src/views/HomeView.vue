<template>
  <div class="main">
    <div class="container">
      <div class="main-intro">
        <p class="main-intro-head">ROOSTERS GAMBLING CLUB</p>
        <p class="main-intro-text yellow">All or nothing</p>
        <p class="main-intro-textarea">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Perferendis
          vero, veritatis velit porro, non at est nobis neque quibusdam optio
          quidem nisi tenetur? Provident sequi maiores omnis inventore eum
          itaque.
        </p>
        <p class="main-intro-textarea">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Perferendis
          vero, veritatis velit porro, non at est nobis neque quibusdam optio
          quidem nisi tenetur? Provident sequi maiores omnis inventore eum
          itaque.
        </p>
        <div class="main-intro-links">
          <a href=""><img src="../assets/img/twitter.png" alt="" /></a>
          <a href=""><img src="../assets/img/discord.png" alt="" /></a>
        </div>
      </div>
      <div class="main-intro-frame">
        <iframe
          src="https://my.spline.design/roostercopy-0882ea22d3e37b0ec342c0c6ae14697e/"
          frameborder="0"
          width="800px"
          height="800px"
        ></iframe>
        <!-- src="https://my.spline.design/roostercopy-0882ea22d3e37b0ec342c0c6ae14697e/" -->
      </div>
    </div>
  </div>
  <div class="info">
    <div class="container">
      <div class="info-image">
        <img src="../assets/img/rooster-info.png" />
      </div>
      <div class="info-text">
        <p class="info-text-main">
          The coolest <span class="yellow">rooster</span> on block
        </p>
        <p class="info-text-textarea">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Reiciendis,
          nemo iure! Omnis asperiores doloremque magnam ab velit corporis
          architecto minima minus error cupiditate? Laborum quam ipsam totam
          ipsum, perspiciatis iusto?
        </p>
        <p class="info-text-textarea">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Reiciendis,
          nemo iure!
        </p>
      </div>
    </div>
  </div>
  <div class="features">
    <div class="container">
      <div class="features-text">
        <p class="features-text-main">
          All holders roosters <span class="yellow">90%</span> profit
        </p>
        <p class="features-text-textarea">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Reiciendis,
          nemo iure! Omnis asperiores doloremque magnam ab velit corporis
          architecto minima minus error cupiditate? Laborum quam ipsam totam
          ipsum, perspiciatis iusto?
        </p>
        <p class="features-text-textarea">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Reiciendis,
          nemo iure!
        </p>
      </div>
      <div class="features-image">
        <img src="../assets/img/eyes.png" />
      </div>
    </div>
  </div>
  <Faq />
  <div class="team">
    <div class="container">
      <div class="team-title yellow">Team</div>
      <div class="team-list">
        <div class="team-list-card">
          <img src="../assets/img/rooster-info.png" />
          <p class="team-list-card-title">Main rooster</p>
          <p class="team-list-card-text">Title</p>
        </div>
        <div class="team-list-card">
          <img src="../assets/img/rooster-developer.png" />
          <p class="team-list-card-title">Developer rooster</p>
          <p class="team-list-card-text">Title</p>
        </div>
        <div class="team-list-card">
          <img src="../assets/img/rooster-developer1.png" />
          <p class="team-list-card-title">Developer rooster jn.</p>
          <p class="team-list-card-text">Title</p>
        </div>
        <div class="team-list-card">
          <img src="../assets/img/rooster-market.png" />
          <p class="team-list-card-title">Co founder rooster</p>
          <p class="team-list-card-text">Title</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Faq from "../components/Faq.vue";

export default {
  components: {
    Faq,
  },
};
</script>

<style lang="scss" scoped>
.main {
  .container {
    max-width: 1380px;
    margin: 0 auto;
    position: relative;
    display: flex;
    justify-content: space-between;
    .main-intro {
      &-head {
        margin-top: 180px;
        font-size: 64px;
        font-weight: 900;
      }
      &-text {
        margin-top: 10px;
        font-size: 32px;
        font-weight: 400;
      }
      &-textarea {
        margin-top: 30px;
        font-size: 19px;
        font-weight: 300;
      }
      &-links {
        display: flex;
        margin-top: 20px;
        gap: 20px;
        a {
          img {
            width: 40px;
            height: 40px;
          }
        }
      }
    }
  }
}
.info {
  padding: 60px 0;
  margin-top: 35px;
  background-color: #15161b;
  .container {
    max-width: 1380px;
    height: 512px;
    margin: 0 auto;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .info-image {
      img {
        width: 512px;
        height: 512px;
        border-radius: 20px;
        box-shadow: 0px 0px 20px #b7c7b977;
      }
    }
    .info-text {
      max-width: 600px;
      &-main {
        font-size: 60px;
        font-weight: 700;
      }
      &-textarea {
        margin-top: 20px;
        font-size: 19px;
        font-weight: 300;
      }
    }
  }
}
.features {
  margin-top: 100px;
  color: #fff;
  .container {
    max-width: 1380px;
    margin: 0 auto;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    .features-text {
      max-width: 900px;
      text-align: center;
      &-main {
        font-size: 60px;
        font-weight: 700;
      }
      &-textarea {
        margin-top: 20px;
        font-size: 19px;
        font-weight: 300;
      }
    }
    .features-image {
      margin-top: 60px;
      img {
        width: 700px;
        height: 200px;
        border-radius: 10px;
        box-shadow: 0px 0px 25px #ffffff46;
      }
    }
  }
}
.team {
  padding: 80px 0;
  color: #fff;
  .container {
    max-width: 1380px;
    margin: 0 auto;
    position: relative;
    display: flex;
    flex-direction: column;
    .team-title {
      text-align: center;
      font-size: 60px;
      font-weight: 700;
      margin-bottom: 80px;
    }
    .team-list {
      width: 100%;
      display: flex;
      justify-content: space-between;
      &-card {
        padding: 20px;
        border-radius: 15px;
        color: #0c0d11;
        text-align: center;
        transition: box-shadow 0.2s;
        img {
          width: 256px;
          height: 256px;
          border-radius: 15px;
        }
        &-title {
          margin-top: 10px;
          font-size: 20px;
          font-weight: 800;
        }
        &-text {
          margin-top: 10px;
          font-size: 18px;
          font-weight: 400;
        }
        &:nth-child(1) {
          background-color: #8d9c8f;
          box-shadow: 0 0 10px #8d9c8f50;
          &:hover {
            box-shadow: 0 0 20px #8d9c8f50;
          }
        }
        &:nth-child(2) {
          background-color: #d1ab10;
          box-shadow: 0 0 10px #d1ab1050;
          &:hover {
            box-shadow: 0 0 20px #d1ab1050;
          }
        }
        &:nth-child(3) {
          background-color: #8a6a7c;
          box-shadow: 0 0 10px #8a6a7c50;
          &:hover {
            box-shadow: 0 0 20px #8a6a7c50;
          }
        }
        &:nth-child(4) {
          background-color: #803062;
          box-shadow: 0 0 10px #80306250;
          &:hover {
            box-shadow: 0 0 20px #80306250;
          }
        }
      }
    }
  }
}
</style>
