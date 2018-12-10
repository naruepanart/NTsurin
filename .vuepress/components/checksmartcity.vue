<template>
  <div>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <td>ชื่อ</td>
    <td>นามสกุล</td>
    <td>ห้อง</td>
    <td>เลขที่</td>
    <tr v-for="total,i in fetchAPI">
      <td>{{total.titlename}}{{total.firstname}}</td>
      <td>{{total.lastname}}</td>
      <td>{{total.classroom}}</td>
      <td>{{total.numberinclassroom}}</td>
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
      .get(
        `https://newapi-ntsurin.herokuapp.com/surinsmartcity/`
      )
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      });
  }

  // Fetches fetchAPI when the component is created.
  /*  mounted() {
    fetch(`https://apiwarpth-zcrbcgqtob.now.sh/fetchAPI`)
      .then(response => response.json())
      .then(fetchAPI => {
        this.fetchAPI = fetchAPI;
        // console.log(fetchAPI);
      });
  } */
};
</script>

<style scoped>
td {
  border: none;
}
</style>