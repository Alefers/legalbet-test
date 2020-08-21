<template>
  <fragment>
    <page-header />
    <main class="content">
      <Matches />
      <BlogsCarousel />
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
  components: {
    BlogsCarousel,
    Matches,
    PageFooter,
    PageHeader
  },
}
</script>
