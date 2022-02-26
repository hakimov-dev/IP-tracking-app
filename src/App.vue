<script>
import axios from 'axios'
import Loader from './components/Loading.vue';
export default {
  created () {
    this.saveData()
  },
  components: {
   Loader
  },
  methods: {
    async saveData(){
      try{
      const { data } = await axios.get('https://api.ipify.org/?format=json')
          //  console.log(data)

           axios.get(`http://ip-api.com/json/${data.ip}`)
           .then(response => {
             console.log(response.data)
             this.data = response.data
             this.ip = response.data.query
             this.city = response.data.city
             this.timezone = response.data.timezone
           })
      } catch(error){
        console.log(error)
      }
    }
  },
  data() {
    return {
      data: null,
      ip: "",
      city: "",
      timezone: "",
      provider: "",
      region: ""
    };
  },
};
</script>

<template>
  <br />
  <!-- This is container -->
  <div class="container">
    <!-- Card 1 -->
    <div class="card center">
      <!-- Title -->
      <h2>Your IP address info</h2>
      <div class="flex card" v-if="data">
        <!-- This is IP address section -->
        <div class="box">
          <span>IP Addres</span>
          <br />
          <span>{{this.ip}}</span>
        </div>
        <div class="box">
          <!-- This is City section -->
          <span>City</span>
          <br />
          <span>{{this.city}}</span>
        </div>
        <!-- This is Timezona section -->
        <div class="box">
          <span>Timezona</span>
          <br />
          <span>{{this.timezone}}</span>
        </div>
      </div>
      <!-- Card 2 -->
      <div class="flex card" v-if="data">
        <!-- This is Provider section -->
        <div class="box">
          <span>Provider</span>
          <br />
          <span>{{this.ip}}</span>
        </div>
        <div class="box">
          <!-- This is Region name section -->
          <span>Region name</span>
          <br />
          <span>{{this.city}}</span>
        </div>
      </div>
      <Loader v-else/>
    </div>
  </div>
</template>

<style>
span {
  display: block;
}

.flex {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  text-align: center;
}

.box {
  width: 35%;
  border-left: 3px solid;
  border-right: 3px solid;
}

.box span:nth-child(1) {
  font-weight: 800;
  font-size: 22px;
}
</style>
