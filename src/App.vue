<template>
  <fragment>
    <Header />
    <main class="content">
      <Matches />
    </main>
    <Footer />
  </fragment>
</template>

<script>
import Header from "./components/application/Header";
import Footer from "./components/application/Footer";
import Matches from "./components/matches/Matches";


export default {
  name: 'App',
  components: {
    Matches,
    Footer,
    Header
  }
}
</script>
