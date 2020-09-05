

<template>
  <div>
     <div class="popular_causes_area section_padding">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-6">
                    <div class="section_title text-center mb-55">
                        <h3><span>Popular Causes</span></h3>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-lg-4" v-for="cause in causes" :key="cause.id">
                    <div class="causes">
                        <div class="single_cause"  >
                            <div class="thumb">
                                <img v-bind:src="cause.thumbnail" alt="">
                            </div>
                            <div class="causes_content">
                                <div class="custom_progress_bar">
                                    <div class="progress">
                                        <div class="progress-bar" role="progressbar" style="width: 0%;" aria-valuenow="30" aria-valuemin="0" aria-valuemax="100">
                                            <span class="progres_count">
                                                {{persentage(cause.fund_raished, cause.goal)}}%
                                            </span>
                                        </div>
                                      </div>
                                </div>
                                <div class="balance d-flex justify-content-between align-items-center">
                                    <span>Deficiency: {{cause.fund_raished}} </span>
                                    <span>Goal: {{cause.goal}} </span>
                                </div>
                                <h4>{{cause.title}}</h4>
                                <p>{{cause.description}}</p>
                                <router-link :to="{name:'detail', params:{id:cause.id}}" class="read_more">Read More</router-link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'Populer',
  data:()=>{
      return {
          causes: [],
          persentage(raised,target){
             return Math.round(1/ (target/raised) * 100)
        }

      }
  },
  mounted(){
      fetch('http://localhost:8000/api/v1/cause')
        .then(res => res.json())
        .then(res => {
            this.causes = res.data
        })
  },
  computed: {

  }
}
</script>