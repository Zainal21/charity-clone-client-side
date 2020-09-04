<template>
  <div class="home">
    <Header />
    <Bradcam title="About"/>
    <Reason/>
    <Activity/>
    <Reason/>
    <Volunter/>
    <Footer/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import Bradcam from '@/components/Bradcam.vue'
import Activity from '@/components/Activity.vue'
import Reason from '@/components/Reason.vue'
import Volunter from '@/components/Volunter.vue'

export default {
  name: 'Home',
  components:{
    Header,
    Footer,
    Bradcam,
    Activity,
    Reason,
    Volunter
  }
}
</script>
