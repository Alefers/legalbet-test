<template>
  <fragment>
    <page-header :screen-type="screenType" />
    <main class="content">
      <matches :screen-type="screenType" />
      <blogs-carousel />
    </main>
    <page-footer />
  </fragment>
</template>

<script>
import PageHeader from "./components/application/PageHeader";
import PageFooter from "./components/application/PageFooter";
import Matches from "./components/matches/Matches";
import BlogsCarousel from "./components/blogs/BlogsCarousel";

export default {
  name: 'App',
  data: () => {
    return {
      screenType: 'desktop',
      allowCountingResize: true
    }
  },
  components: {
    BlogsCarousel,
    Matches,
    PageFooter,
    PageHeader
  },
  created() {
    window.addEventListener("resize", this.resizeHandler);
    this.resizeHandler();
  },
  methods: {
    resizeHandler() {
      if (this.allowCountingResize) {
        this.allowCountingResize = false;
        setTimeout(() => {
          this.setScreenType();
          this.allowCountingResize = true;
        }, 50);
      }
    },
    setScreenType() {
      if (window.matchMedia("(max-width: 767px)").matches && this.screenType !== 'mobile') {
        this.screenType = 'mobile';
      }
      if (window.matchMedia("(min-width: 768px) and (max-width: 1199px)").matches && this.screenType !== 'tablet') {
        this.screenType = 'tablet';
      }
      if (window.matchMedia("(min-width: 1200px)").matches && this.screenType !== 'desktop') {
        this.screenType = 'desktop';
      }
    }
  }
}
</script>
