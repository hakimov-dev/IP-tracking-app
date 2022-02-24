<script>
import axios from 'axios'
export default {
  created () {
    this.saveData()
  },
  methods: {
    async saveData(){
      try{
      const { data } = await axios.get('https://api.ipify.org/?format=json')
           console.log(data)
      } catch(error){
        console.log(error)
      }
    }
  },
  data() {
    return {
      ip: "",
      city: "",
      region: "",
      country: "",
      timezone: "",
    };
  },
};
</script>

<template>
  <br />
  <div class="container">
    <div class="card center">
      <h2>Your IP address info</h2>
      <div class="flex card">
        <div class="box">
          <span>Hello</span>
          <br />
          <span>1111</span>
        </div>
        <div class="box">
          <span>Hello</span>
          <br />
          <span>1111</span>
        </div>
        <div class="box">
          <span>Hello</span>
          <br />
          <span>1111</span>
        </div>
        <div class="box">
          <span>Hello</span>
          <br />
          <span>1111</span>
        </div>
        <div class="box">
          <span>Hello</span>
          <br />
          <span>1111</span>
        </div>
      </div>
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
  width: 25%;
  border-left: 3px solid;
  border-right: 3px solid;
}

.box span:nth-child(1) {
  /* color: ; */
  font-weight: 800;
  font-size: 22px;
}
</style>
