<template>
  <section class="offers container my30 px15 cl-black">
    <div class="row">
      <div
        class="offer-container col-xs-12 col-sm-4 pb15"
        v-for="(banner, index) in banners.mainBanners"
        :key="index"
      >
        <router-link :to="localizedRoute(banner.link)">
          <div class="offer" v-lazy:background-image="banner.image">
            <h3 class="title m0 h2" style="color:white">
              {{ banner.title }}
            </h3>
          </div>
        </router-link>
      </div>
    </div>
  </section>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "PromotedOffers",
  props: {
    singleBanner: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  computed: {
    ...mapGetters({
      banners: "promoted/getPromotedOffers",
    }),
  },
  async created() {
    await this.updatePromotedOffers();
  },
  methods: {
    ...mapActions({
      updatePromotedOffers: "promoted/updatePromotedOffers",
    }),
  },
};
</script>

<style lang="scss" scoped>
.offer-container {
  &:last-child {
    padding-bottom: 0;
  }
}
.offer {
  height: 435px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  opacity: 1;
  transition: 0.3s all;

  &:hover {
    opacity: 0.9;
  }

  @media (max-width: 767px) {
    height: 200px;
  }

  .title {
    text-align: center;
    margin-top: 2rem;
    @media (max-width: 767px) {
      background-color: rgba(255, 255, 255, 0.4);
      padding: 0.5rem;
      line-height: 2.4rem;
    }
  }

  .subtitle {
    font-family: "Roboto", sans-serif;
    @media (max-width: 767px) {
      background-color: rgba(255, 255, 255, 0.4);
      padding: 0.5rem;
    }
  }
}
.offer-small {
  height: 360px;

  @media (max-width: 767px) {
    height: 200px;
  }
}
.offer-product {
  height: 330px;
  background-position: 50% 20%;

  @media (max-width: 767px) {
    height: 330px;
  }
}
.title {
  @media (max-width: 767px) {
    font-size: 36px;
  }
}
.subtitle {
  @media (max-width: 767px) {
    font-size: 18px;
  }
}
</style>
