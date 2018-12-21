<template>
  <div>
    <p>จำนวนทีมที่ส่ง : {{fetchAPI.length}} ทีม</p>

    <div v-for="total,i in fetchAPI">
    <b>{{total.group}} - ห้อง {{total.classroom}}</b>
      <p>{{total.profiles.titlename1}} {{total.profiles.firstname1}} {{total.profiles.lastname1}}
      - เลขที่ {{total.profiles.numberinclassroom1}} - (ประธาน) <br>

      {{total.profiles.titlename2}} {{total.profiles.firstname2}} {{total.profiles.lastname2}}
      - เลขที่ {{total.profiles.numberinclassroom2}} - (รองประธาน) <br>

      {{total.profiles.titlename3}} {{total.profiles.firstname3}} {{total.profiles.lastname3}}
      - เลขที่ {{total.profiles.numberinclassroom3}} - (กรรมการ) <br>

      {{total.profiles.titlename4}} {{total.profiles.firstname4}} {{total.profiles.lastname4}}
      - เลขที่ {{total.profiles.numberinclassroom4}} - (กรรมการ) <br>

      {{total.profiles.titlename5}} {{total.profiles.firstname5}} {{total.profiles.lastname5}}
      - เลขที่ {{total.profiles.numberinclassroom5}} - (กรรมการ) <br>

      {{total.profiles.titlename6}} {{total.profiles.firstname6}} {{total.profiles.lastname6}}
      - เลขที่ {{total.profiles.numberinclassroom6}} - (กรรมการ) </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      fetchAPI: ""
    };
  },
  mounted() {
    axios
      .get(`https://newapi-ntsurin.herokuapp.com/regtechnopreneur/`)
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      })
      .catch(function(error) {
        console.log(error);
      });
  }

};
</script>

<style scoped>
td {
  border: none;
}
</style>
