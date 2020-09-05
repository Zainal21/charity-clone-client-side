<template>
  <div>
     <div class="popular_causes_area pt-120 cause_details ">
        <div class="container">
            <div class="row">
                <div class="col-lg-12 col-md-12">
                    <div class="single_cause">
                        <div class="thumb">
                            <img v-bind:src="cause.thumbnail"  alt="">
                        </div>
                        <div class="causes_content">
                            <div class="custom_progress_bar">
                                <div class="progress">
                                    <div class="progress-bar" role="progressbar" style="width: 30%;" aria-valuenow="30" aria-valuemin="0" aria-valuemax="100">
                                        <span class="progres_count">
                                            30%
                                        </span>
                                    </div>
                                  </div>
                            </div>
                            <div class="balance d-flex justify-content-between align-items-center">
                                <span>Raised: $5000.00 </span>
                                <span>Goal:{{cause.goal}} </span>
                            </div>
                            <h4>{{cause.title}}</h4>
                            <p>{{cause.description}}</p> 
                        </div> 
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="make_donation_area section_padding">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-lg-6">
                    <div class="section_title text-center mb-55">
                        <h3><span>Make a Donation</span></h3>
                    </div>
                </div>
            </div>
            <div class="row justify-content-center">
                <div class="col-lg-6">
                    <form class="donation_form"  v-on:submit.prevent="addDonation()">
                        <div class="single_amount">
                            <div class="input_field mt-4">
                                <div class="input-group">
                                    <div class="input-group-prepend">
                                        <span class="input-group-text" id="basic-addon1">Name</span>
                                    </div>
                                    <input type="hidden" class="form-control" placeholder="40,200" aria-label="Username" aria-describedby="basic-addon1">
                                    <input type="text" class="form-control" placeholder="40,200" aria-label="Username" aria-describedby="basic-addon1" v-model="name">
                                </div>
                                <div class="input-group mt-4">
                                    <div class="input-group-prepend">
                                        <span class="input-group-text" id="basic-addon1">Amount</span>
                                    </div>
                                    <input type="text" class="form-control" placeholder="40,200 in Rupiah" aria-label="Username" aria-describedby="basic-addon1" v-model="donation">
                                </div>
                                <div class="input-group mt-4">
                                    <div class="input-group-prepend">
                                        <span class="input-group-text" id="basic-addon1">Email</span>
                                    </div>
                                    <input type="text" class="form-control" placeholder="example@awesome.com" aria-label="Username" aria-describedby="basic-addon1" v-model="email">
                                </div>
                                <button type="submit" class="btn boxed-btn mt-5">Donate Now</button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>
<script>
import swal from 'sweetalert';
export default {
  name:'SingleCause',
  data:() => {
    return {
      cause :[],
      name: null,
      email:null,
      donation:null,
    }
  },
  mounted(){
    let id = this.$route.params.id
    fetch(`http://localhost:8000/api/v1/cause/${id}`)
      .then(ress => ress.json())
      .then(ress => {
        this.cause = ress.data
      })
  },
  methods:{
    
    addDonation(){
      //  let id = this.$route.params.id
      fetch(`http://localhost:8000/api/v1/donation`,{
        method:'POST',
        headers:{
          "Content-Type": 'application/json',
          "Accept": 'application/json',

        },
        body: JSON.stringify({
          causes_id : this.$route.params.id,
          name: this.name,
          email: this.email,
          total_donation: this.donation,
        })
      }).then(ress => ress.json())
      .then(ress => {
       swal({
          title: "Donasi Berhasil!",
          text: "Terimakasih Banyak Atas Dukungan Anda!",
          icon: "success",
          button: "Ok!",
        })
        console.log(ress)
          this.name= ''
          this.email= ''
          this.donation= ''
      })
    }
  }
}
</script>

