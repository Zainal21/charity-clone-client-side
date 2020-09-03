<template>
  <div class="home">
    <Header />
    <Slider/>
    <Reason/>
    <Populer/>
    <Footer/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/Header.vue'
import Slider from '@/components/Slider.vue'
import Reason from '@/components/Reason.vue'
import Populer from '@/components/Populer.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'Home',
  components:{
    Header,
    Slider,
    Reason,
    Populer,
    Footer
  }
}
</script>
