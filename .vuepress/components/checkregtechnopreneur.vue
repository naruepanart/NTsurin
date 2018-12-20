<template>
  <div>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <td>กลุ่มที่</td>
    <td>ชื่อ</td>
    <td>นามสกุล</td>
    <td>ห้อง</td>
    <td>เลขที่</td>
    <tr v-for="total,i in fetchAPI">
    <td>{{total.group}}</td>
      <td>{{total.profiles.titlename1}}{{total.profiles.firstname1}}</td>
      <td>{{total.profiles.lastname1}}</td>
      <td>{{total.classroom}}</td>
      <td>{{total.profiles.numberinclassroom1}}</td>
    </tr>
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
