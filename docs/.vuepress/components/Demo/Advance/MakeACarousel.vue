<template>
  <div class="carousel-wrap">
    <vuescroll-carousel :type="type">
      <div
        class="child"
        v-for="i in 5"
        :key="i"
      >
        <span class="carousel-text">
          Slide{{i}}.
        </span>
      </div>
    </vuescroll-carousel>
  </div>
</template>

<script>
import vuescrollCarousel from 'vuescroll-carousel';
export default {
  props: {
    type: {
      type: String,
      default: 'h'
    }
  },
  components: { vuescrollCarousel },
  computed: {
    typeDesc() {
      return this.type != 'h' ? 'vertical' : 'horizontal';
    }
  },
  data() {
    return {};
  }
};
</script>

<style lang="stylus" scoped>
.carousel-wrap {
  width: 100%;
  border: 1px solid rgba(91, 140, 255, 0.3);

  .child {
    width: 100%;
    text-align: center;
    text-shadow: 0px 3px 3px #975a00;
    -webkit-text-shadow: 0px 3px 3px #975a00;
    -moz-text-shadow: 0px 3px 3px #975a00;
    font-family: '微软雅黑 Bold', '微软雅黑 Regular', '微软雅黑';
    font-weight: 700;
    font-style: normal;
    font-size: 48px;
    color: #ff9900;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>