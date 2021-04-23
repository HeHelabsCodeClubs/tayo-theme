<template>
  <section class="head-image w-100 bg-cl-th-accent cl-white">
    <div
      class="container w-100 h-100"
      v-lazy:background-image="currentImage.image"
      v-if="currentImage"
    >
      <div class="head-image-content">
        <div class="align-center">
          <h3 data-testid="mainSliderSubtitle">
            {{ currentImage.subtitle }}
          </h3>
          <h1 data-testid="mainSliderTitle">
            {{ currentImage.title }}
          </h1>
          <div class="align-center inline-flex">
            <button-outline
              :link="currentImage.link"
              color="light"
              class="button"
            >
              {{ currentImage.button_text }}
            </button-outline>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
// import ButtonOutline from 'theme/components/theme/ButtonOutline'
import { mapGetters } from "vuex";

export default {
  components: {
    // ButtonOutline
  },
  data() {
    return {};
  },
  computed: {
    ...mapGetters({
      currentImage: "promoted/getHeadImage",
    }),
  },
};
</script>

<style lang="scss" scoped>
.head-image {
  display: none;
  background: black;
  overflow: hidden;
  @media (min-width: 767px) {
    display: inherit;
  }

  .head-image-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-left: 40%;
    padding-top: 8%;

    .title {
      font-size: 3.4rem;
      margin-bottom: 0;
    }

    .subtitle {
      font-size: 0.8rem;
      max-width: 340px;
      font-family: "Roboto", sans-serif;
      line-height: 1.2rem;
    }
  }
}

.head-image {
  height: 640px;
}
.container {
  background-size: cover;
  background-position: bottom center;
  background-repeat: no-repeat;
}
.button {
  background-color: #fff;
  color: #000;
  border: none;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
.row {
  height: 640px;
}
@media (max-width: 75em) {
  .head-image {
    height: 400px;
  }
  .title {
    font-size: 50px;
  }
  .subtitle {
    font-size: 20px;
  }
  .button {
    background-color: #fff;
    color: #000;
    border: none;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
  }
  .row {
    height: 400px;
  }
}
@media (max-width: 64em) {
  .head-image {
    height: 359px;
  }
  .container {
    background-position: left;
  }
  .title {
    font-size: 48px;
  }
  .subtitle {
    font-size: 18px;
  }
  .button {
    background-color: #fff;
    color: #000;
    border: none;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
  }
  .row {
    height: 359px;
  }
}
</style>
