<template>
  <div class="home">
    <Header />
    <Bradcam title="Detail Cause"/>
    <SingleCause/>
    <Footer/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import Bradcam from '@/components/Bradcam.vue'
import SingleCause from '@/components/SingleCause.vue'

export default {
  name: 'Home',
  components:{
    Header,
    Footer,
    Bradcam,
    SingleCause,
  }
}
</script>
