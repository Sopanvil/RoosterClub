<template>
  <div class="faq">
    <div class="container">
      <div class="faq-title"><span class="yellow">FAQ</span>`s</div>
      <div
        v-for="(item, index) in faqs"
        :key="index"
        class="faq-list"
        :class="{ open: item.show }"
        @click="openFaq(index)"
      >
        <p class="faq-list-title">
          {{ item.title }}
        </p>
        <div class="faq-list-text">
          {{ item.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      faqs: [
        {
          show: false,
          title: "How many ROOSTERS are available?",
          text: "1 111",
        },
        {
          show: false,
          title: "What is the mint price?",
          text: "0.35 SOL",
        },
        {
          show: false,
          title: "When is the launch?",
          text: "Launch Date and Time : TBA",
        },
        {
          show: false,
          title: "Where will be the listing?",
          text: "We will list on MAGICEDEN after Sold Out",
        },
        {
          show: false,
          title: "How do I get a rooster?",
          text: "The link of the mint will be provided in at MINT TIME",
        },
      ],
    };
  },
  methods: {
    openFaq(index) {
      // this.faqs[id].show = !this.faqs[id].show
      this.faqs = this.faqs.map((faq, i) => {
        if (index === i) {
          faq.show = !faq.show;
        } else {
          faq.show = false;
        }
        return faq;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.faq {
  padding: 60px 0 80px 0;
  .container {
    max-width: 900px;
    margin: 0 auto;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    .faq-title {
      text-align: center;
      font-size: 60px;
      font-weight: 700;
      margin-bottom: 60px;
    }
    .faq-list {
      padding: 15px;
      transition: 0.3s;
      border-bottom: 1px solid #ffffff50;
      max-height: 65px;
      overflow: hidden;
      transition: max-height 0.5s, background-color 0.3s;
      &:nth-child(2) {
        border-radius: 15px 15px 0 0;
      }
      &:hover {
        cursor: pointer;
        background-color: #ffffff10;
      }
      &.open {
        max-height: 200px;
      }
      &-title {
        font-size: 30px;
        font-weight: 400;
      }
      &-text {
        margin-top: 20px;
        font-weight: 300;
        font-size: 19px;
      }
    }
  }
}
</style>