<template>
  <div class="home">
    <Header />
    <Bradcam title="Contact"/>
    <Message/>
    <Footer/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import Bradcam from '@/components/Bradcam.vue'
import Message from '@/components/Message.vue'

export default {
  name: 'Home',
  components:{
    Header,
    Footer,
    Bradcam,
    Message
  }
}
</script>
